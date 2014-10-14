(* Before you run this script you will need:

- The latest version of Spotify for Mac installed;
- Messages set up with an iCloud account on both your Mac and iOS device;
- To start a conversation with your own mobile number or iCloud email;
- In the code below replace [Your Phone Number Here] with your mobile number or iCloud email associated with your iOS device.
*)


activate application "Spotify"
delay 1

--Grabs all the track information from Spotify
tell application "Spotify"
	set theTrack to name of the current track
	set theArtist to artist of the current track
	set theAlbum to album of the current track
	set track_id to id of current track
end tell

--builds the Spotify URL
set AppleScript's text item delimiters to ":"
set track_id to third text item of track_id
set AppleScript's text item delimiters to {""}
set realurl to ("spotify://track:" & track_id)

--Builds and sends the Spotify URL to the Clipboard
set theString to theTrack & " - " & theArtist & ": " & realurl
set the clipboard to theString

--Tells Messages to send the Spotify URL to your mobile number or iCloud email
tell application "Messages"
	set myid to get id of first service
	set theBuddy to buddy "4022381644" of service id myid
	send theString to theBuddy
end tell

--Get your groove on