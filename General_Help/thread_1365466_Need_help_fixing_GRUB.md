---
title: "Need help fixing GRUB"
date: 2009-12-27
forum: General Help
---

### Post by epsilonvector on 2009-12-27
I have the following scenario: 
Dual booting Ubuntu with Windows 7.
Had 3 main partitions: the Windows partition, the Linux partition, and a 6GB system restore partition that had installation files for Windows Vista (came with the computer). 
I wanted to reclaim the space of that third partition for the Windows one, so I went to the Windows partition manager and deleted it. I then discovered that I can't merge it because the Linux partition is in between, and that I need to do this with Gparted. Fine. I restart in order to load Ubuntu, and now I get Error 17. 

Please help me fix this. 
Note: I have an old Ubuntu cd somewhere (6.10 I believe).

---

### Post by mprice on 2009-12-27
This might help you fix your problem.

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)

---

### Post by epsilonvector on 2009-12-27
Will this also make Windows bootable?
And is there a more automatic way to do this?

---

### Post by epsilonvector on 2009-12-27
...anyone?

---

### Post by RedSingularity on 2009-12-27
Try this command,

sudo update-grub

---

### Post by SecretCode on 2009-12-27
There probably isn't much of an automatic way. But if you're not sure what you are doing, best to ask! We'll need to see exactly how your disk is laid out ...

Try your ubuntu 6.10 CD, but it would be better if you can download and burn a 9.04 or 9.10 live cd, and/or a rescue CD like a recent PartedMagic.

Boot to the live CD and run
```
sudo fdisk -lu
```

Post the output here (in code tags - use the # button.)

---

