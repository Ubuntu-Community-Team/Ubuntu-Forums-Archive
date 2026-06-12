---
title: "Change boot startup from Windows XP"
date: 2011-02-21
forum: General Help
---

### Post by sriwebads on 2011-02-21
Dear Friends,
I'm using dual OS (XP and Ubuntu 10.04) and i have been using ubuntu for past a year, now i have a problem when booting, that i made by mistake.

I use Windows XP only to work with Photoshop other than that i mostly use Ubuntu for everything. Recently my windows xp got crashed, so without any idea i have reinstalled windows xp but now i cann't able to find my ubuntu. i don't know what to do right now?

Am i required to reinstall ubuntu (my most of the files are in ubuntu), is there any solution without reinstall.

I find that need to change the boot.ini, but i'm not getting any proper results, please help me.

Note: **Need to Change the booting from windows XP to promting for Ubuntu and Windows XP**

---

### Post by deconstrained on 2011-02-21
Did you delete your Ubuntu partition? Or did you just reinstall XP on the same existing Windows partition?

---

### Post by wilee-nilee on 2011-02-21
Boot a live Ubuntu cd and run this command and post the results.
fdisk -lu

---

### Post by sriwebads on 2011-02-21
> **deconstrained said:**
> Did you delete your Ubuntu partition? Or did you just reinstall XP on the same existing Windows partition?
I did delete the Ubuntu partition, just reinstall Windows XP

---

### Post by sriwebads on 2011-02-21
> **wilee-nilee said:**
> Boot a live Ubuntu cd and run this command and post the results.
fdisk -lu
I have Ubuntu 9.10 is that okay

---

### Post by deconstrained on 2011-02-21
> **sriwebads said:**
> I did delete the Ubuntu partition
Oops... :(
Since you deleted the Ubuntu partition, your data is gone, unless you use some kind of professional data recovery tool to read the bits off the deleted partition.

Backup, backup, backup.

Edit: wilee-nilee's suggestion is still worth a shot, and should work with a 9.10 disk.

---

### Post by sriwebads on 2011-02-21
Sorry, i didn't delete the Ubuntu partition (not even touch it), i have just installed Windows XP only.

Please check the attached images for details

---

### Post by sriwebads on 2011-02-21
Sorry, i didn't delete the Ubuntu partition (not even touch it), i have just installed Windows XP only.

Please check the attached images for details

---

### Post by deconstrained on 2011-02-21
> **sriwebads said:**
> Sorry, i didn't delete the Ubuntu partition (not even touch it), i have just installed Windows XP only.

Please check the attached images for details
Is that 180 GB partition Ubuntu? If it is, then....

FANTASTIC! That means you don't even have to reinstall Ubuntu, you just need to reinstall Grub to the master boot record so that you can dual-boot again. There's a wiki article on it here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by sriwebads on 2011-02-21
Okay, i will try as per the document mentioned, if i'm facing any problem i will let you know my friend.

---

