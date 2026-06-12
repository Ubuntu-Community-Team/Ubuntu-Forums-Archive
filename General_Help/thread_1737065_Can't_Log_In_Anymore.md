---
title: "Can't Log In Anymore"
date: 2011-04-23
forum: General Help
---

### Post by LonelyAspie on 2011-04-23
Whenever I try to log in, it, shows a black screen and goes right back tot the log in screen again. I does this everytime. I even tried restarting my laptop but that didn't work. 

Before this happened, I was going to copy some songs that I have updated to my jump drive and for some reason, all the files showed a lock on them, so I tried editing the setting (permission settings), I set one to blank, not knwong what I was doing and the other to everything or something. After I clicked OK, a large number of blank popup boxes came up on my screen and my screen froze. I restarted and couldn't log in. I not had this problem before. The recent songs where downloaded from Youtube and converted to MP3 using WinFF on Ubuntu.

I now  have Ubuntu installed on a sperate HDD, I am able to access the files from my other HDD (the one where I can't log into) and access the files and copy them over to this HDD. Also, I tried the jump drive on this one and was able to copy the songs to this HDD perfectly. There were no lock symbles on the  files. Kinda strange. Not sure what was different about Ubuntu onthe other HDD to make Lock symbles appear on the icons. BTW, it was only on the jump drive, that I had plugged into.

---

### Post by bmathis on 2011-04-23
Sounds like a permissions issue. Boot to recovery mode and check who owns your home dir.
```
ls -l /home
```
if its not owned by your username then, and someone needs to chime in here to verify my help, chmod your home dir
```
chmod -R username:username /home/username
```

---

### Post by LonelyAspie on 2011-04-23
How do I get into recovery mode?

---

### Post by bmathis on 2011-04-23
Reboot... when grub comes up it'll ask what you want to boot into, select recover mode.

---

### Post by LonelyAspie on 2011-04-23
> **LonelyAspie said:**
> How do I get into recovery mode?

I don't get anything, it just automatically boots in. Nothing in the BIOS to select GRUB. I only get that when I have more then 1 kernels, but also always delete the previous ones when I upgrade.

---

### Post by urckle on 2011-05-30
eh shouldn't that be:
```
chown
``` instead of chmod? :-/

---

### Post by zzzz401 on 2011-05-30
My computer has had some weird grub issues my resolution is off on the grub with my monitor witch is a tv 40inch. Maybe you might be having that same problem on yours that is why it won't show up..](*,)](*,)

---

### Post by LonelyAspie on 2011-07-07
I had this happen on another hard drive, I installed Ubuntu where it says replace it with the one on the CD, and it worked, and didn't lose anything. I just had to install my apps again.

---

