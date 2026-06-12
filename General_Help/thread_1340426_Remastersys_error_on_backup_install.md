---
title: "Remastersys error on backup install"
date: 2009-11-28
forum: General Help
---

### Post by nexoncore on 2009-11-28
[B]Problem
[/B]When choosing to install from backup, it installs up to 94% then errors with the following error.

"cant install grub-pc on /target/"

After this error, the installer stops. When rebooting grub fails and falls to command line and the install from the remastersys backup in fully inaccessible.

[B]Already Tried
[/B]- Producing another backup and testing ( Same Error )
- Upgrading to latest version ( Same Error )

Currently running ubuntu 9.10 with remastersys 2.0.13-1 on grub 1.97beta

---

### Post by nexoncore on 2009-11-28
Anyone?

---

### Post by hariprasad on 2009-12-06
I have the same problem, Ubuntu 9.10 x86-64 Remastersys 94%: "The 'grub-pc' package failed to install into /target. Wihout the GRUB boot loader, the installed system will not boot.

---

### Post by sume on 2010-02-04
> **hariprasad said:**
> I have the same problem, Ubuntu 9.10 x86-64 Remastersys 94%: "The 'grub-pc' package failed to install into /target. Wihout the GRUB boot loader, the installed system will not boot.

Did you manage to resolve this? I'm having the same problem

---

### Post by pmbsa on 2010-06-05
same problem  here, anybody got any ideas? are there viable alternatives to remastersys?

---

### Post by qazwertopij on 2010-06-06
I have the same issue

---

### Post by R33D3M33R on 2010-08-20
I have the same problem on Lucid Lynx. I have contacted the author about this issue, but haven't received any reply. So if anyone is registered on the geekconnection forums -> please report this. Thanks.

---

### Post by the blackbull on 2010-10-02
Remastersys v 2.0.17.1 works OK with Ubuntu 9.10 and 10.04 (tested)

---

### Post by llaimu on 2010-12-12
I have the same problem with the 2.0.17-1 version. Remastersys make the iso but when i install i have the same problem with grub. If I ignore the error I can boot the installed SO only with Grub Rescue CD. This is a trouble with Grub 2.0, I think. Any idea to solve it?

---

### Post by Icche Ghuri on 2011-01-16
I have the same problem. My Ubuntu version is 10.04.1 and Remastersys-2.0.17-1.

Did you all installed BURG in your system? Cause I did, and I was wondering, if it created this problem! :|

---

### Post by mike555 on 2011-01-16
You mast have ubiquity and ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment.before making a backup ..........I don't know if that is your problem , but was mine.......

---

### Post by Icche Ghuri on 2011-01-17
> **mike555 said:**
> You mast have ubiquity and ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment.before making a backup ..........I don't know if that is your problem , but was mine.......

I'm using Ubuntu 10.04.1, gnome desktop environment. I have already installed ubiquity and ubiquity-frontend-gtk, but not the third one. Since I'm not using KDE environment I think I'm ok with that. But still it doesn't solve the problem.

---

### Post by Huss on 2011-02-22
I have a similar problem - custom install gets to the end, then fails at Grub install. Now when I reboot it only loads into GNU grub prompt. 

How can I get my system up and running again?

So far I have tried:
- Run live cd (10.10-64), mount the drive of the failed install and reinstall grub. I have only tried this with my custom dist as the original distribution hangs on the splash screen.
- Boot using grub prompt - entering kernel image, initrd and uuid. This hangs shortly after.
- Run windows recovery cd and reinstall MBR

This is on a: dual boot - windows and Ubuntu. AMD, ATI

Your help would be appreciated

---

### Post by Huss on 2011-02-23
Just had to format and start again :(. I hope remastersys has been updated since I cerated my iso.

---

### Post by Tshady on 2011-06-17
Went through the same problem like you all had.  Digged through Google and found this work-around.  You will have to build a grub bootloader from a live CD.  I followed NYbill's direction:

[http://crunchbanglinux.org/forums/topic/7024/grub-failed-to-install-statler-a-workaround/](http://crunchbanglinux.org/forums/topic/7024/grub-failed-to-install-statler-a-workaround/)

Worked great!  Try it out.  Good luck.

---

