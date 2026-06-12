---
title: "Boot option removal"
date: 2010-08-07
forum: General Help
---

### Post by reialist on 2010-08-07
Hi, I just brought a HP mini 311 it came with Windows XP since its not supported in Ubuntu (Wubi 10.04 Didn't work) I decided to install Windows 7 the install worked but now I have a boot menu of dead operating systems 1.Window's XP which doesn't work i deleted the Windows.old file to get rid of it that didn't even work, 2.Jolicloud which was installed Within Windows XP & Windows 7 which i want to keep.

How do I deleted these so it just goes straight into Windows 7?

*P.S. it's not GRUB*

---

### Post by Jesus_Valdez on 2010-08-07
The Win 7 CD (or DVD) should come with a restore mbr option.

---

### Post by viper250 on 2010-08-07
xp,vista,and win7 use lilo bootloader 
many linux distros also use it
you have to edit the lilo configuration file to remove the old os entry

---

### Post by reialist on 2010-08-07
> **viper250 said:**
> xp,vista,and win7 use lilo bootloader 
many linux distros also use it
you have to edit the lilo configuration file to remove the old os entry

I don't think Window's uses LiLo, LiLo stands for Linux Loader.

From what I know windows use's MBR (Master Boot Record).

Is it possible to fix the MBR without using the CD drive as I'm using a Netbook.

---

### Post by varunendra on 2010-08-08
If you can boot into windows 7, use bcdedit command from there to restore windows MBR

*I think MBR is a generic term, not windows specific*

---

### Post by cariboo on 2010-08-08
This isn't an Ubuntu support question, you will probably get better help [here]("http://h30434.www3.hp.com/"). This thread is closed.

---

