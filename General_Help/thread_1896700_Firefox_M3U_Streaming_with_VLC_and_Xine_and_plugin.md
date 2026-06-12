---
title: "Firefox M3U Streaming with VLC and Xine and plugins"
date: 2011-12-17
forum: General Help
---

### Post by wmccarty on 2011-12-17
This is not a request for help.

I solved a seemingly simple problem today and would like to provide details on how I solved it.

For the last little while I was unable to play M3U streaming from on-line radio stations with Firefox. I had to copy the URL into VLC and hit play that way. Since I use Xmarks to save all my radio stations, this became a little annoying as it is an extra few steps when all you want is to just press one link.

What I found is that if you have VLC and XINE plug-ins installed they will both try to grab the M3U extension even if you have the file type in Firefox pointing to VLC.

- Open Firefox Add-Ons
- Go to Plug-ins
- Disable Xine plug-in
 (this is if you would like to keep the Xine media player on your system, sometimes it plays content that other players cannot)
- Close the tab
- Open Preferences
- Go to Applications
- Go to MPEG Audio URL
- Set the file to always open with VLC
- If it is not on the list, point it to /usr/bin/vlc or qvlc

You should now be able to play the M3U file as you may not have been before.

---

