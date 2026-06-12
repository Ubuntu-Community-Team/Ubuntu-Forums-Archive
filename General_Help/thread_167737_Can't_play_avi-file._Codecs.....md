---
title: "Can't play avi-file. Codecs...."
date: 2006-04-29
forum: General Help
---

### Post by UbuntuUbuntu7 on 2006-04-29
Hello, i have some problem with a avi-file that i cant play. I use xine. It doesnt work in mplayer or vlc either, though. After som research it seems that i need the "xine-win32" codec. When i try to play the file in xine i get this message: **"There is no demuxer plugin avaliable to handle _bla bla bla(the file path)_. Usually this means that the file format was not recognized"**. But i can play other avi-files. Its just this particular file. 

I found another post:


[I]"I know that in PCLinuxOS and Mandriva that I had to install MPlayer, and win 32-codecs, **xine-win32**, real-codecs from PLF and mplayer-plugins and xmms-alsa from Contrib but I cannot find them anywhere in Synaptic.
How do people watch a video or listen to some sound in Ubuntu is beyond me at the moment."
[/I]
How do i get the xine-win32 codec and the other codecs? Do i need in some way to clean out all the codecs and start over again? How do i do? Anybody know? :confused:

---

### Post by rez on 2006-04-29
Hi there.  I'm not sure what codecs you have installed, but I've found the script at the link below pretty useful for installing basically all the codecs I've needed so far.  Although, I think one or two .avi or .wmv formats I've tried afterwards still have issues.

[http://www.ubuntuforums.org/showthread.php?t=157589&page=3](http://www.ubuntuforums.org/showthread.php?t=157589&page=3)

I suggest you give that thread a quick read for the installation steps, then give it a go ;)

Good luck!

---

### Post by croak77 on 2006-04-29
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Perfect Storm on 2006-04-29
You might take a look at source-o-matic, you'll find the link in my signature.

---

### Post by UbuntuUbuntu7 on 2006-04-29
Nah, don't work.

---

### Post by barisurum on 2006-04-29
I couldnt play them at start too. You must look for a plugin to gstreamer in synaptic and if there is one about AVI install it. if this doesnt work there is a package called "w32codecs". maybe you cannot find it in indexes of synaptic, but you can find a DEB package on the net. search for it and install it.

if you dont know how to install deb packages

  go to the directory of the package:

  sudo dpkg -i w32codecs.deb

---

### Post by UbuntuUbuntu7 on 2006-04-29
Ok thanks for the answers so long lads. I have this file, called essential-20050412.tar.bz2, but when i try to unpack it to the codecs folders i get the message that i don't have the permission to pack it up in that folder.

---

### Post by Perfect Storm on 2006-04-29
If you followed the source-o-matic link which helps you setting up your sourcelist (adding PLF).
The only thing you have to do is
```
sudo apt-get install w32codecs
```

Or try Automatix or Easy Ubuntu

---

### Post by UbuntuUbuntu7 on 2006-04-29
Won't work.

---

### Post by UbuntuUbuntu7 on 2006-04-29
:-k :confused:

---

### Post by croak77 on 2006-04-29
wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

  sudo dpkg -i w32codecs_20050412-0.0_i386.deb

---

### Post by UbuntuUbuntu7 on 2006-05-01
Nope.

---

### Post by croak77 on 2006-05-01
What do you mean nope? Nope it didn't download? Nope it didn't install? Nope it didn't play?

---

### Post by kupajava on 2006-05-01
heh heh, "what do you mean nope" that's hilarious, you remind me of my dad when I was growing up in NY... classic...

Anyway, I saw this in an earlier post, but have you tried automatix, if you tell it to give you the non-free codecs it gives you like a cubic-crapload of them.  Ive been able to play some crazee old stuff with them no-problem.  If not, have you been able to play whatever file you are trying with anything?  Definately try playing the file on another machine with a different distribution (or windows if you can stomach it...) and see if their might be something wrong with the file in question.  I know this sounds silly but sometimes silly works.  Otherwise, try VLC or Totem or something and see if you can get that to work cuz hey, this is Linux, and there are 80 ways to skin a cat here, and they are all free...

---

