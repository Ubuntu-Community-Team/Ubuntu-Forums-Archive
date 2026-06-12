---
title: "The package google-talkplugin needs to be reinstalled, but I can't find an archive fo"
date: 2010-12-23
forum: General Help
---

### Post by HitmanNumber86 on 2010-12-23
E: The package google-talkplugin needs to be reinstalled, but I can't find an archive for it.

I downloaded the .deb from Google and it seemed to lock up in the middle of the install. I had to kill it. Now, I can't get apt-get to do anything.

Code:
hitmannumber86@Faptop-357:~$ sudo apt-get clean
hitmannumber86@Faptop-357:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hitmannumber86@Faptop-357:~$ sudo dpkg --configure -a
hitmannumber86@Faptop-357:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-talkplugin needs to be reinstalled, but I can't find an archive for it.


I found a similar problem on the forums. 
[http://ubuntuforums.org/showthread.php?t=1641894&highlight=package+reinstalled+can't+find+archive](http://ubuntuforums.org/showthread.php?t=1641894&highlight=package+reinstalled+can't+find+archive) 
But, being a novice, I don't want to go poking around sensitive areas.

---

### Post by HitmanNumber86 on 2010-12-23
Is there any way of doing this without poking around in the kernel? Last time I tried fixing an install package I succeeded, but the next time I started my computer the bootloader, methinks, screwed up and I didn't know how to reinstall it. I learned alot from that mistake, like ALWAYS keep a USB startupdisk handy.

---

### Post by AlphaLexman on 2010-12-23
Where did you download the file? For me, it was in '~/Downloads' you could run:
```
sudo dpkg -i google-talkplugin_current_i386.deb
```

---

### Post by meghsinghnokha on 2012-06-02
it works i solved my same problem . thanks a lot dear

---

