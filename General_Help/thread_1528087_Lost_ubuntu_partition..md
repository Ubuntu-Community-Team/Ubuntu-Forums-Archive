---
title: "Lost ubuntu partition."
date: 2010-07-10
forum: General Help
---

### Post by Haykuroo on 2010-07-10
Had ubuntu and windows xp running dual-boot, two partitions on the same drive. Could read and write to both partitions from the respective OS.

A few weeks back something went wrong, I think it was the GRUB loader. Can't remember the specifics but I used the windows installation CD to replace the GRUB loader, did not format anything though. Now I'm looking to recover the documents I had on the partition before I format and replace windows with ubuntu on a single partition. 

I'm confident that the partition wasn't formatted, but it is no longer visible in windows explorer etc. I've tried using fs-driver.org "Ext2IFS_1_11a.exe" but that didn't work. :-s

I'm at a complete loss, any help would be greatly appreciated.
Thanks.

---

### Post by spiky001 on 2010-07-10
Have you tried running ubuntu live cd

---

### Post by ronnielsen1 on 2010-07-10
> A few weeks back something went wrong, I think it was the GRUB loader.  Can't remember the specifics but I used the windows installation CD to  replace the GRUB loader, 
As long as you didn't do any partitioning or formatting, you need to use the ubuntu cd to restore grub. Windows won't do it.

You don't say what version of Ubuntu you're using. If it's 10.04

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

If an earlier version of Ubuntu

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Haykuroo on 2010-07-10
Hm, just reading through the recovery documentation. I downloaded "Ext2 Volume Manager" after reading some more, it recognized the partition and assigned it a drive letter but I still cannot access it from windows "The disk is not formatted". Is booting into ubuntu the only way? Thanks.

---

### Post by audiomick on 2010-07-10
> **Haykuroo said:**
> ... Is booting into ubuntu the only way? Thanks.

Don't know if it is the only way, but it might be the easiest.
Since you are planning to format the whole drive, you presumably have an external drive or another computer to save your stuff off onto.

If you boot into the live CD (the try without changing the computer option on the install CD), you should be able to move off any files you want to save, both from the Ubuntu installation, and, as far as I know, the windows installation.

---

### Post by Haykuroo on 2010-07-10
> **audiomick said:**
> Don't know if it is the only way, but it might be the easiest.
Since you are planning to format the whole drive, you presumably have an external drive or another computer to save your stuff off onto.

If you boot into the live CD (the try without changing the computer option on the install CD), you should be able to move off any files you want to save, both from the Ubuntu installation, and, as far as I know, the windows installation.

Was just thinking something along those lines myself :)
Thanks for your help guys!

---

### Post by Haykuroo on 2010-07-10
Damn. Booted to Live CD (latest release) and it wouldnt read the partition :(
Any ideas? I've got some screenshots if it'll help.

---

### Post by meoconvn38 on 2010-07-10
maybe you need hiren's boot cd, then using fdisk tool to fix this, after that you can see ur partition:popcorn:

---

### Post by Haykuroo on 2010-07-27
Bump :(

---

### Post by dino99 on 2010-07-27
boot on external prog like partedmagic and prepare your partitions before installing

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

