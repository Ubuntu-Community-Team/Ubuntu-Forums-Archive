---
title: "Trying to reinstall GRUB.. Keep getting an error 15"
date: 2011-08-29
forum: General Help
---

### Post by Graysonh on 2011-08-29
Hey there,

I'm still pretty new to Ubuntu and Linux in general so please go easy on me if the answer to this problem is simple.

I have Ubuntu installed on a 64GB SSD in my laptop. I partitioned the HDD and installed Windows 8 (7989). Now, when I go to reinstall GRUB as per the instructions I found online I get "Error 15: File not found".

This is what I'm trying to run.
```
sudo grub
grub> find /boot/grub/stage1
```

Ref: [http://forums.techarena.in/operating-systems/1142140.htm]("http://forums.techarena.in/operating-systems/1142140.htm") Post #4

What can I do to successfully reinstall GRUB so I can get my Ubuntu booting again?

Thanks for your time.

---

### Post by saltmarshlamb on 2011-08-29
Those are instructions for dealing with grub legacy.

Ubuntu uses Grub2 now - [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by seawolf167 on 2011-08-29
If for some reason the instructions from saltmarshlamb's post still error out for you (they should work), try purging and re-installing Grub 2 per [these instructions]("http://ubuntuforums.org/showthread.php?t=1581099").

---

### Post by ReptilianShadow on 2011-08-29
As mentioned by the other posts, boot repair should work to reinstall grub2. 
Here's a link to the ubuntu documentation on boot-repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
These instructions worked fine for me when I deleted my Ubuntu partition then reinstalled Ubuntu (11.04), with a dual boot of Windows 7.

---

### Post by Graysonh on 2011-08-29
Thank you my friends :)

---

### Post by seawolf167 on 2011-08-29
If it is all working now, please mark this thread as Solved under Thread Tools.

---

