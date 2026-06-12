---
title: "How to disable linux recovery entry in burg"
date: 2010-08-07
forum: General Help
---

### Post by TJEnger on 2010-08-07
**Recently installed burg themes for grub 2. A little unimpressed with the included themes (anyone know where to find additional themes?), but oh well.**
 
**My biggest gripe, however, is I can't seem to prevent it from displaying the Ubuntu recovery option. I prefer a very clean look and have removed previous kernels and removed the executable bit from the memtest to prevent those options from appearing, however even after uncommenting the ****GRUB_DISABLE_LINUX_RECOVERY=true line in /etc/default/grub and updating, burg still shows the recovery option in the menu. Ugh!**
 
**Anyone know a way to prevent it from displaying???**
 
**Thanks!**

---

### Post by xXxBlender3DxXx on 2010-08-07
The dirty way to do it is to edit the burg.cfg file manually and delete the Recovery entry. This will stay in effect until you update BURG.

About themes, just make your own. I edited sora_clean to include some custom images and a background. It's not hard at all.

---

### Post by dshosu on 2010-08-09
From everything I've read so far about about grub2 and burg that last thing I think you want to do is modify the .cfg file.

I think the problem is that you are updating /etc/default/**grub** and not /etc/default/**burg**.

Add "GRUB_DISABLE_LINUX_RECOVERY=true" to /etc/default/**burg** and I think it should work.

*I would wait for a confirmation from another more experience user if I were you but I'm pretty sure that's what the problem is.

---

### Post by dcstar on 2010-08-10
> **TJEnger said:**
> Recently installed burg themes for grub 2. A little unimpressed with the included themes (anyone know where to find additional themes?), but oh well.
 
My biggest gripe, however, is I can't seem to prevent it from displaying the Ubuntu recovery option.
........
Anyone know a way to prevent it from displaying???
 
Thanks!

Apart from pressing the "F" key?

[https://code.google.com/p/burg/wiki/InstallUbuntu](https://code.google.com/p/burg/wiki/InstallUbuntu)

PS Do not use formatting to gain attention when posting questions.

---

