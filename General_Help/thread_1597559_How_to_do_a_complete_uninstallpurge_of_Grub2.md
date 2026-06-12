---
title: "How to do a complete uninstall/purge of Grub2?"
date: 2010-10-15
forum: General Help
---

### Post by auh2o on 2010-10-15
When upgrading to Maverick I accidentally (yes, I know, my bad) installed Grub to my Ubuntu partition instead of to the MBR. It was already installed to the MBR prior to this. So, when I rebooted all I got was the Grub rescue console. I loaded the Linux image with a different boot loader on floppy instead, and proceeded to uninstall and reinstall Grub2 to MBR with 

```
sudo apt-get purge grub-common grub-pc
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub
```However, on restart I now get the regular Grub console, but not the selection screen to select what to boot. This even though all Linux kernel images and the Windows 7 partition I have was found during the reinstall. So, seems I need to do a complete purge of Grub from both MBR and sda3 (which is the Ubuntu partition i accidentally chose on upgrade), and start over clean. Question is then, how do I do it, line by line from the terminal?

---

### Post by TeoBigusGeekus on 2010-10-15
Have you tried to install grub to the hd you want?
When at grub prompt
```
grub>setup (hd0)
```
Replace hd0 with your preferred hd.

---

### Post by oldfred on 2010-10-15
this has many solutions:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

HOWTO: Purge and Reinstall Grub 2 from the Live CD -drs305
In cases where the boot info script results look normal, we usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
reinstall & purge of grub.
[http://ubuntuforums.org/showthread.php?t=1350856](http://ubuntuforums.org/showthread.php?t=1350856)

---

### Post by auh2o on 2010-10-20
Thank you oldfred. The solution to my problem was simply:

```
sudo dpkg-reconfigure grub-pc
```And then untick sda3 and choose sda instead. Finished with

```
sudo grub-install --recheck /dev/sda
sudo update-grub
```...and everything worked on reboot! Marking as solved.

---

