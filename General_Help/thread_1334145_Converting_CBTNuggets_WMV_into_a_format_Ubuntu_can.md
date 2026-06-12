---
title: "Converting CBTNuggets WMV into a format Ubuntu can read"
date: 2009-11-22
forum: General Help
---

### Post by madfrenzy on 2009-11-22
Hi all,
I've been trying to get CBTNuggets videos to work on ubuntu for some time now but it wouldnt work so I was wondering if there was a program or a way to convert those WMVs to a format that Ubuntu can read (hopefully to the same size or less).

Thanks in advance
Mina Makary

---

### Post by mike555 on 2009-11-22
you should be able to view WMV ,if you have the "restricted extras" installed.........

---

### Post by madfrenzy on 2009-11-22
I have installed the restricted extras but it doesnt work, I will upload a video and post the link so you can test it yourself

---

### Post by madfrenzy on 2009-11-22
I choose the smallest video its about 1.9 MB and here is the link : [http://www.4shared.com/file/157208909/b0a88e76/ccent31.html](http://www.4shared.com/file/157208909/b0a88e76/ccent31.html)



PS: To Moderators If this violates any forum rules or policy please notify me and I'll remove it at once and sorry if it is.

---

### Post by madfrenzy on 2009-11-22
Anybody??

---

### Post by mc4man on 2009-11-22
It's a mms2 video (microsoft screen codec) with wma speech audio

If you are on a 32 bit install then mplayer will plackback fine with the addition of w32codecs

32codecs can be gotten from medibuntu, see here how to add to sources, then install the codecs.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As far as mplayer you have many choices both for mplayer itself and frontend gui's, try the repo one for starters.

screen shows your video in gnome-mplayer which is a simple frontend that works well in karmic, smplayer also works fine in any ubuntu release

---

### Post by madfrenzy on 2009-11-22
Thank you for your reply, you are a life saver :). I have ubuntu 9.10 64-bit and installed the w64codecs and gnome-player but it still cant work, any ideas??

---

### Post by mc4man on 2009-11-22
see link, your choices are probably limited to building and installing a 32 bit mplayer (which can be used for most uses as a full replacement for the 64 bit version (a bit of work to do
or
installing a windows mplayer that runs thru wine (takes about 5 min., can be used for local playback of files that your 64 bit players can't handle, gui only

Possible issue with the win player/wine in karmic - as noted only oss worked as audio setting in winecfg, otherwise I've seen something about about a wine pulseaudio patch though haven't investigated

[http://ubuntuforums.org/showthread.php?p=8191113#post8191113](http://ubuntuforums.org/showthread.php?p=8191113#post8191113)

---

