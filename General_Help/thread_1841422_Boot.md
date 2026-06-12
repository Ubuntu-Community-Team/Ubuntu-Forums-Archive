---
title: "Boot"
date: 2011-09-09
forum: General Help
---

### Post by aeathb on 2011-09-09
So I was hoping someone could help with an issue on the boot. I tried searching for an answer but I couldnt tell if some of the fixes scratched all the old files. On Boot up I get a blank screen on startup (I'm on 11.04 natty). Booting up from the live CD I don't see anything in var/crash....... If there are no easy fixes I want to grab my files on that partition and when I load from the live cd I "dont have permission" to get to my main folder where all my files are. So in turn im asking 2 questions. I think its too broad of question to ask any help with "fixing" the current ubuntu (I guess ill just reinstall), but the second question of how to get my old files I would appreiciate some advise for! 

Thanks,

Austin

---

### Post by dino99 on 2011-09-09
on top of this subforum: see the sticky for workaround

[https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Bblankscreen&ie=utf-8&oe=utf-8](https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Bblankscreen&ie=utf-8&oe=utf-8)

---

### Post by oldfred on 2011-09-09
I think older versions mounted all partitions with full permissions. Now they do not. Ubuntu does not have a password so just use sudo and enter on password. Just be careful as you have full rights to do as much damage as you want.
From terminal
```

sudo nautilus
```

Do you get grub menu or if only one system, holding down shift key from BIOS until menu appears. Then it is not a boot issue but probably a video issue or possibly some other driver. I always have to use nomodeset on grub menu entry on first boot until I get nVidia driver installed. Nomodeset works for some other video cards.

If you can get to menu try recovery mode.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by aeathb on 2011-09-09
I am a novice so I will read up on those and try to decode what it means....As an update, I think you may be right about a graphics issue because I can't even get the livecd to come up and load anymore. I REALLY REALLY do'nt want to go back to this windows junk. I never realized how slow it is.....

---

### Post by aeathb on 2011-09-09
To explain, I only really need to get a file because I have a 16 page thesis on mycoherbicides saved ubuntu and its due tomorrow!! I do NOT want to write anything that boring twice in my life.... I tried holding shift during every possible screen and no menu is coming up. Also, when I try to boot up safe mode to get into safe graphics mode i keep getting a "panic error rebooting in 30 seconds." I am lost....

---

