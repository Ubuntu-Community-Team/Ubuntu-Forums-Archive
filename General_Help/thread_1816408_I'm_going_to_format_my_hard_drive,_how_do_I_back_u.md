---
title: "I'm going to format my hard drive, how do I back up just Ubuntu?"
date: 2011-08-01
forum: General Help
---

### Post by mx597turbo on 2011-08-01
I installed in this order: WinXP, Win7, Ubuntu 11.04. Win7 no longer works, and I don't use XP.

I want to format the drive and just install Win7 and Ubuntu. I will have to reinstall 7, but I would like to copy Ubuntu as it is right now. How can I do this? Should I use CloneZilla on the Ubuntu partition? If I do this, how would I set up the bootloader? I never worked with a bootloader before, so please be detailed if you can. Thanks in advance.

---

### Post by varunendra on 2011-08-02
> **mx597turbo said:**
> I installed in this order: WinXP, Win7, Ubuntu 11.04. Win7 no longer works, and I don't use XP.

I want to format the drive and just install Win7 and Ubuntu. I will have to reinstall 7, but I would like to copy Ubuntu as it is right now. How can I do this? Should I use CloneZilla on the Ubuntu partition? If I do this, how would I set up the bootloader? I never worked with a bootloader before, so please be detailed if you can. Thanks in advance.
Try remastersys. Clone zilla will just copy the partition with partition's boot sector, but it won't touch the MBR if it is not an 'entire disk' image. So you'll need to install grub manually later. That's not a problem. See this guide or ask here in case of problems.

However, remastersys will create a live DVD of your installation (just make sure to move all unnecessary files from your home directory to reduce backup size), which you can use in both live mode and can restore/install it also. But it will fail if the backup size (after compression) exceeds the size of DVD (4.4 GB).

I've once witnessed problem with suggested installation method on remastersys's website ([http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)). In that case, you can manually install the .deb package from here: [http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb)
(although this package is meant for Karmik (ubuntu 9.10), but it worked fine on 11.04).

If it created your backup DVD iso successfully, you can write a DVD from it to reinstall it on any computer just like normal Ubuntu live CD. Choose 'backup' mode to preserve all your user files and settings (including password).

---

