---
title: "no sound 9.10"
date: 2009-12-05
forum: General Help
---

### Post by muse3332 on 2009-12-05
[SIZE=4][COLOR=Green]hi, i have ubuntu 9.10 and im dual booting it with windows xp i requested the live cd from the website and so i installed it but now theres no sound what do i do?[/COLOR][/SIZE] i have no idead what hardwerre i have sorry

---

### Post by fluffman86 on 2009-12-05
This may sound weird, but is your sound muted?  Look for a speaker icon next to the clock.  If it's not muted, try messing around in the preferences.  If you still can't get it, go to Applications > Accessories > Terminal and type

alsamixer

That will let you adjust some sound levels with the arrow keys.  Press "M" to mute or unmute channels, and press "Q" to quit.

---

### Post by muse3332 on 2009-12-05
ok i did and it did this "function snd_ctl_open failed for default: No such file or directory"

---

### Post by svinoba on 2009-12-05
> **muse3332 said:**
> ok i did and it did this "function snd_ctl_open failed for default: No such file or directory"
For the above error, some (including me on another distro) have got success by running the following```
sudo chmod 777 /dev/snd/* 
```Try it and see if it helps. 

Follow this thread too. [http://ubuntuforums.org/showthread.php?t=1094196](http://ubuntuforums.org/showthread.php?t=1094196)

---

