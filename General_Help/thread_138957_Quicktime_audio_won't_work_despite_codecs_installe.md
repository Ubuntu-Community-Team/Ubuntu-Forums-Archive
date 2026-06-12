---
title: "Quicktime audio won't work despite codecs installed?"
date: 2006-03-02
forum: General Help
---

### Post by ChrisC on 2006-03-02
I'm trying to play a downloaded MOV.

If I run totem at the command line, specifying the file, it says:

** Message: don't know how to handle video/x-svq, svqversion=(int)3, codec_data=(buffer)0000007f7374736400000000000000010000006f53565133000000000000000100031380534d4920000003ff0000020000f000b4004800000048000000000000000110536f72656e736f6e20566964656f20330000000000000000000000000000000018ffff00000015534d49205345514800000005e1e0169d8000000000, width=(int)240, height=(int)180, framerate=(double)12
** Message: don't know how to handle audio/x-gst-fourcc-Qclp, rate=(int)8000, channels=(int)1

... and nothing plays at all. 

If I run it in mplayer, I get the video (!) but no audio, and I get a popup error saying that it couldn't handle audio "0x706C6351".  Some googling led me to believe that this is "QuickTime QCLP audio decoder" and should by handled by mplayer's "QuickTime.qts" codec file.

I've installed libquicktime1 in Synaptic, searched in this forum, checked ubuntuguide, googled ... It seems that I need the w32codecs package but nothing I try (repositories added) seems to work -- it's never shown in the available package list.  Which repository works, with breezy, *today*?

I'd prefer a solution that gets it working in mplayer, as I've had nothing but failure and frustration in previous battles with totem.  Help!

---

### Post by akiro.yamamoto on 2006-03-02
This post outlines the installation of the w32codecs package as well as the Mplayer
Plugin that allows embedded play in Firefox.
[http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)
Hope this helps.
D

---

### Post by ChrisC on 2006-03-03
Thanks!  I shudder at the deb file download method instead of synaptic/repository method, but I really want this MOV to work (it's from a subscription service that I paid for).  OK, so I have audio now.  But now the video is jumpy.

I can't wait for dapper to come out and magically make all my problems go away ... they will all go away, right?  And no new problems will appear, right?  :)

---

### Post by ComputerExpertVK on 2008-06-24
i get something like error 0x706C6351 in audio when playing quicktime files in mplayer
it plays the file but no audio

---

