---
title: "Installing Vista over Ubuntu 10.04"
date: 2010-07-15
forum: General Help
---

### Post by 1Nick1 on 2010-07-15
Hi, I just stuffed up my computer and I had to install Ubuntu as there was no other option.
Now I need to reinstall Vista (I have a CD) but I want to also wipe Ubuntu.
Thanks for any help.

---

### Post by AceRoom on 2010-07-15
Any particular reason why you don't want to dual-boot? You can have both Windows (Any one) and Linux at the same time. You can choose the boot option at startup.

Anyway, if you must remove Linux, you boot from you Windows cd/dvd and delete the Ubuntu partition from the partition manager in Windows Setup. You can then reparition you hard disk in any way you like. Choose one partition for the new C:\
Then proceed as normally as any Windows Installation. Windows will remove GRUB.

---

### Post by 1Nick1 on 2010-07-15
> **AceRoom said:**
> Any particular reason why you don't want to dual-boot? You can have both Windows (Any one) and Linux at the same time. You can choose the boot option at startup.

Anyway, if you must remove Linux, you boot from you Windows cd/dvd and delete the Ubuntu partition from the partition manager in Windows Setup. You can then reparition you hard disk in any way you like. Choose one partition for the new C:\
Then proceed as normally as any Windows Installation. Windows will remove GRUB.

I will dual boot, but please explain this more clearly.;)

---

### Post by AceRoom on 2010-07-15
Just search here on the forums or on google on how to install windows after Ubuntu. You'll get plenty of good results.

Installing Windows will spoil your GRUB, so after installing Windows, you can either reinstall only GRUB or reinstall Ubuntu in its entirety. For the first option, there are plenty of guides.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 1Nick1 on 2010-07-15
> **AceRoom said:**
> Just search here on the forums or on google on how to install windows after Ubuntu. You'll get plenty of good results.

Installing Windows will spoil your GRUB, so after installing Windows, you can either reinstall only GRUB or reinstall Ubuntu in its entirety. For the first option, there are plenty of guides.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I do not know if you know what I mean.
I need to install windows. Linux is currently my only OS.
Thanks.:P

---

### Post by sigixv on 2010-07-15
Easiest way: If you want to install windows only - and you have your backup/install disk - just install it as you normally would.

If you would like to use linux also in a dual boot (=having windows AND linux on the same machine at the same time), install it afterwards by just following the instructions given by the installer

---

### Post by Braik on 2010-07-15
I think AceRoom answered you in the best way, you have to install windows as if your computer was brand new (follow windows installation CD instructions), take care not to destroy your ubuntu partition/installation, after that you should just re-install grub as in the link he proposed you.

---

### Post by sigixv on 2010-07-15
--- Making a clean install of windows will erase all data on your hard disk as it gets formatted. Be sure to backup everything if you do so...

---

