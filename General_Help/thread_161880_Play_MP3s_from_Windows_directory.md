---
title: "Play MP3s from Windows directory?"
date: 2006-04-17
forum: General Help
---

### Post by Charlie Mopps on 2006-04-17
I have several windowsXP based computers on my network. They share resorces via several shared folders. Primarily I share a large MP3 collection between them. I have a computer that I use to play the MP3s though a stereo in my livingroom. Last night I got a BSD on that machine with a DLL error... and knew it was a "re-install windows"  type of problem. 

Rather than bother with that I put Ubuntu on it. I don' tplay games on that machine so it seemed a good candidate for Linux. The one thing I haven't been able to get it to do is play Mp3s from my shared folder. I can navigate to my mp3 folder... But I can' tplay any Mp3s from it.

I would like to know what would be a good MP3 player that could read the Samba mounted Windows shared folder, load all the Mp3s, scan that folder on a regular basis for new files and then finally play those Mp3s when I wanted it to. I am very used to winamp. Any help would be appretiated.

---

### Post by jazzmuzik on 2006-04-17
xmms and beep media player (bmp) are very similar to winamp. You have to add some repositories to get the mp3 libraries. Search on 'mp3' for help setting it up. amaroK is a nice player, but I haven't used it that much. mplayer is great for playing anything from the command line.

---

### Post by Qrk on 2006-04-17
A great guide is in System->Help-> 5.10 starter guide. Look under multimedia for most of your needs. For more, look here:

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Iandefor on 2006-04-18
Handy formatting tip, to avoid confusion:

BSD = Berkeley Software Distribution
BSOD = Blue Screen Of Death

Ubuntu can't play MP3's by default. MP3's are patent-encumbered and would mean that a part of the base system couldn't be redistributed with complete freedom- which is against the idea of Ubuntu. You can definitely install support for them, though. Check the link Qrk gave, it's pretty handy.

---

### Post by Charlie Mopps on 2006-04-18
[QUOTE=Iandefor]
Ubuntu can't play MP3's by default. MP3's are patent-encumbered and would mean that a part of the base system couldn't be redistributed with complete freedom- which is against the idea of Ubuntu. [/QUOTE]

Pfft... I hate copywrite law... grrrr

---

### Post by lcg on 2006-04-18
[QUOTE=Charlie Mopps]Pfft... I hate copywrite law... grrrr[/QUOTE]
Copyright laws aren't such a bad thing. In this case, the problem comes from software patents. **They** mostly are a bad thing!

You could always have a look at Ogg Vorbis, an open source lossy audio codec, which can be used free of charge and even has better sound quality (at the same size) compared to MP3. The only downside is that you have to rip all your CDs again (as transcoding from MP3 to Ogg Vorbis is a bad idea).

HTH,
Lars

---

### Post by helvete on 2006-09-04
on a similar note i have shared access to my mp3 folder on my windows box, but amarok can only play file located on the local machine is there any way to create a link on the local machine that would allow the folder to be seen on the local machine?

---

