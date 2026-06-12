---
title: "sounds are gone"
date: 2006-05-18
forum: General Help
---

### Post by shredfitz on 2006-05-18
Hello.  Noob here.  Love ubuntu.  This is the problem though :  I have been having issues with sound and have searched these forums in an attempt to solve them and now it seems that I have done something to ruin my sound altogether.  Previously I cuold get sound out of xmms and totem sometimes, I could never get streaming audio from the likes of youtube or streaming real player, so I sought out a solution and tried some suggestions and now I have no sound whatsoever and I have no idea where to start.  Please, I am clueless as to where to begin to resolve these issues.

---

### Post by shredfitz on 2006-05-18
okay .....I am able to get sound back to xmms.  still cannot get streaming audio from youtube, google video, real player.  Still cannot get sound from totem

---

### Post by Sef on 2006-05-18
> This is the problem though : I have been having issues with sound and have searched these forums in an attempt to solve them and now it seems that I have done something to ruin my sound altogether.

1) What exactly did you do?  Could you please be more specific in what you tried?

2) Did you download the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Sef on 2006-05-18
The codecs should take care of most if it.  To get sound from Youtube, you need to do this:

Applications > Accessories > Terminal

sudo apt-get update

sudo apt-get install alsa-oss

---

### Post by shredfitz on 2006-05-18
brian@ubuntu:~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree... Done
alsa-oss is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems



still doesn't work

---

