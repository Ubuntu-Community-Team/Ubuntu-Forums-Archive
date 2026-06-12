---
title: "How can I make MPlayer as default player?"
date: 2006-05-02
forum: General Help
---

### Post by SwaroopKunduru on 2006-05-02
I installed MPlayer and it is working fine on my system. How can I make it as a default player. 

When I click on video on net I am getting totem and complains it doesn't play. I wanted to run that video in MPlayer insted of Totem.

:confused: 

Regards,

Swaroop Kunduru.

---

### Post by r4ik on 2006-05-02
If Firefox is your browser try,

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

7.17

Good luck !

---

### Post by BarFly on 2006-05-02
Okay, it is easy.  I did it to switch from Totem to VLC as default.  Right click on the file and go into properties.  Go to "open with" and select whatever you want to use.

On a side note, VLC is refusing to show the video for some WMV files, so I still have Totem as a back up.

Oh, sorry.  You mean embedded videos on the internet.  I do not know.  Yes, it annoys the heck out of me that some movies insist on using Totem.

You are supposed to be able to do it by going into Firefox Edit Preferences Downloads.  I give up.  Anyone care to answer?

---

### Post by nanotube on 2006-05-02
well, install the mplayer plugin for firefox (if you are using firefox to browse), and that would set mplayer to be the default embedded player.

---

### Post by Hoffmann on 2006-05-02
[QUOTE=SwaroopKunduru]I installed MPlayer and it is working fine on my system. How can I make it as a default player. 

When I click on video on net I am getting totem and complains it doesn't play. I wanted to run that video in MPlayer insted of Totem.

:confused: 

Regards,

Swaroop Kunduru.[/QUOTE]

Try this:

First go to System tab ---> Preferences ---> Removable Drives and Media
Then, switch to Multimedia tab in Removable Drives and Media. In the Video DVD Disc write this in the commandline box:

gmplayer dvd://1 -dvd-device /dev/dvd 

Hoffmann

---

### Post by FerGeCo on 2006-05-08
Thanks! this is what i needed (:

---

