---
title: "Ubuntu and windows 7 after...?"
date: 2009-11-29
forum: General Help
---

### Post by chaiyz on 2009-11-29
I've been using Ubuntu 9.0.4 for the past few months.  I ordered windows 7 and when it arrived I installed it and have been running it for over a month.  

Today I decieded to try to get grub back and realized I'd lost my liveCD.  I saw a new version available and downloaded and burned the CD.

I was then able to reinstall grub and get my 9.0.4 installation back and then upgraded it to 9.10.  

Now I'm stuck and don't know how to get grub to see the 7 install.  No grub OS choices just a 3 second timeout and back to 9.10.  

It's been a month and I'm sure it's something simple I'm forgetting but I'm stumped.  

Any advice to get me dualbooting 9.10 and 7 would be appreciated.  

BTW, my ubuntu is on sda1 and windows 7 is on sda3.

Thanks,

Chaiyz

---

### Post by fluffman86 on 2009-11-29
hold shift while your computer is booting, just before the grub menu comes up.

---

### Post by omnipotentperson on 2009-11-29
You need to edit your /boot/grub/menu.lst (grub menu configuration) so that there is a windows 7 option. There are lots of other threads on the forums about this, and I'm sure you can find one about your specific problem.

You probably need to add something like 
```
title		Windows 7 (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by lidex on 2009-11-30
menu.lst is not used in Karmic. Read these pages:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

