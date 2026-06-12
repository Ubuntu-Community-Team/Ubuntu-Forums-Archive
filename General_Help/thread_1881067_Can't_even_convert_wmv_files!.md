---
title: "Can't even convert wmv files!?"
date: 2011-11-14
forum: General Help
---

### Post by altjx on 2011-11-14
I've been going through hell and back on Linux just simply trying to play wmv files. I've had other threads with no solutions, never ran across a solution, etc... whatever.

So here I am trying to convert a .wmv file to an .avi file using ffmpeg and WinFF (GUI for ffmpeg).. But I am getting an error. This has to be one of the most annoying things ever. Can anyone help me out with this?

It's almost like I have to keep Windows VM up & running my entire time for backup stuff that dont or nevr works.

EDIT: Nevermind. Can't even convert it on Windows.

---

### Post by andrew.46 on 2011-11-15
Can you post the troublesome wmv file somewhere?

---

### Post by altjx on 2011-11-15
> **andrew.46 said:**
> Can you post the troublesome wmv file somewhere?

I just watched it in VMware on Win 7.. Didn't have the patience. Thanks though!

---

### Post by linuxwin2 on 2011-11-15
> **altjx said:**
> I just watched it in VMware on Win 7.. Didn't have the patience. Thanks though!
:)

With mplayer you can play wmv files.

---

### Post by Jouke74 on 2011-11-15
And Handbrake should be able to convert them for you, or Avidemux...

---

### Post by altjx on 2011-11-15
> **linuxwin2 said:**
> :)

With mplayer you can play wmv files.

I went through hell in another thread trying to get this to work. Never got it either.

---

### Post by 3rdalbum on 2011-11-15
This might seem obvious, but some people don't understand. You must actually have WMV playback support working in order to be able to convert from WMV. The 'non-free-codecs' package in the Medibuntu repository will ensure you have the necessary support.

Yes, some people have thought "Oh, I can't play WMV... so I'll try converting it to something else instead on Ubuntu!".

---

### Post by Steve54 on 2011-11-15
VLC will play just about any file you throw at it. It can also transcode to other formats

---

### Post by carranty on 2011-11-15
> **Steve54 said:**
> VLC will play just about any file you throw at it. It can also transcode to other formats

+1, I've never found a media filetype vlc can't play, it's the bee's knees :)

---

### Post by mister_p_1998 on 2011-11-15
Make sure you've installed the Ubuntu-restricted-extras and If you want it to play more smoothly, I'd convert to mpg with mobile-media-converter

---

### Post by raja.genupula on 2011-11-15
you can use[Mobile media converter ]("http://www.miksoft.net/mobileMediaConverterDown.htm") to convert wma files to mp3 format or avi format and to many formats.

---

### Post by BillyBoa on 2011-11-15
There are four WMA codecs and Windows Media Audio (WMA) is the most common. So maybe your file is not even recognized from Windows media player.

---

### Post by Chronon on 2011-11-15
I doubt that any of the players on Ubuntu will work if the files are encumbered by DRM.

---

