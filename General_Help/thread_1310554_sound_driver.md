---
title: "sound driver"
date: 2009-11-01
forum: General Help
---

### Post by xbeefsupreme on 2009-11-01
I have just recently installed 64 bit Ubuntu 9.04 on my Hp pavillion dv6z-1100.  However, I have not been able to get the sound to work, it will not work for mp3s, youtube videos or games.  I've made sure that the sound wasn't muted and cannot find a linux driver on HP's website.  Any suggestions will be appriceated.

---

### Post by dbyjazz on 2009-11-01
Go to sound preferences and try messing around with your hardware profile. like mine right now is set as 'Analog Stereo Duplex'

also try downloading GNOME Alsa Mixer

---

### Post by TheForumTroll on 2009-11-01
You might find something here:
[https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard]("https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard")

---

### Post by xbeefsupreme on 2009-11-01
Thanks for the suggestions, unfortunately nothing has worked.  If it helps, i ran the "lspci" command and got the following for sound device:

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

---

### Post by TheForumTroll on 2009-11-02
Well, it's not the same sound chip but you might find something [in this thread]("http://ubuntuforums.org/showthread.php?t=1308926") where someone is trying to fix sound problems too.

---

