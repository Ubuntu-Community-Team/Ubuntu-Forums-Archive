---
title: "stuck in GRUB line-editing"
date: 2011-08-11
forum: General Help
---

### Post by gepolv on 2011-08-11
-----------update solved!----
The reason is restart cannot work correctly so I force to turn off my computer which might cause wubi corrupt. When I manually reboot, windows7 moved c:ubuntu/disks/ folder to somewhere else. So I have to use the method described in:
[http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html](http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html) to restore that folder. After it is restored, I can boot my wubi ubuntu smoothly.
-----------------------------
Hey, all!
My ubuntu (11.04) (win7+wubi) suddenly cannot boot and is stuck in  GRUB line-editing.

The information showed is:

--------------------------------------
GNU GRUB version 1.99~rc1--13 ubuntu3
[ Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions]
grub> 
--------------------------------------

when I input
grub> ls
(hd0) (hd0,7) (hd0,6) (hd0,5) (hd0,3) (hd0,2) (hd0,1)
grub> ls -la
device hd0: partition table
  partition hd0,7: partition type NTFS UUID(some number)
  partition hd0,6: partition type NTFS label FUUID(some number)
  partition hd0,5: partition type NTFS label EUUID(some number)
  partition hd0,3: partition type NTFS label OS(some number)
  partition hd0,2: partition type NTFS label recoveryUUID(some number)
  partition hd0,1: partition type NTFS label DELLUTILITY UUID(some number)


I have tried many different ways and it seems no one can really work. 
---------------------update-----------------
I cannot find "c:/ubuntu/disks" folder!??? But the total used capacity of C is still the same.
---------------------------------------------


Could some help me out?

Thanks
Gepo

---

### Post by gepolv on 2011-08-11
any help? Please.

---

