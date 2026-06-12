---
title: "error GNOME Power Manager have not been installed correctly"
date: 2010-04-23
forum: General Help
---

### Post by John122 on 2010-04-23
I have a Asus 1005pe and tried to follow the instructions here; [http://ubuntuforums.org/showthread.php?p=8874600#post8874600](http://ubuntuforums.org/showthread.php?p=8874600#post8874600) to make the screen dimming work. My line had the work splash so I left it there so my line looked like “[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"[/FONT][/COLOR]”
 

 However when I rebooted next time I got: “Install problem The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact our computer administrator.” And it will not let me log in. It just gives this error every time I try to log in.
 

 So I booted to the recovery mode and changed my line back to “[COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]” and ran sudo update-grub2 again but it still has the same problem. Any idea what I can do to fix this? I am leaving for a few days in a few hours and would like to have it working by then. Thanks for your help.

---

### Post by John122 on 2010-04-23
Because of what is said here [http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/) I "sudo apt-get clean" and it did not seem to do any thing, so I booted to the live ubuntu cd and made the root partition that was twice as big (extenede it), but there was an error and I ended up with a partition that was twice as big but had the same amount of free space (180mb). So I booted up to the recovery ubuntu (from the grub screen) and ran the disk test that it pops up but it came back fine. I can still boot to the log in screen and ctrl-alt-f1 to a command line and log in there. I am backing up now (with cp). I was running a backup before this all happend (I thin k it was with simple backup manager or something like that, it has two parts, manage, restore). What can I remove safly remove form the root partition? The home partition is seperat. Thanks

---

### Post by John122 on 2010-04-26
Any ideas were to go from here. Thanks

---

### Post by John122 on 2010-04-27
Booted up to another live cd and rezised the partiton. Some how by the magic of linux all my free space came back. One thing I found out is Ubuntu will not let you log in if there is less then 180mb of free space. Not sure why that is but I think it is some thing that should be changed. It would be best if we could boot and log into a system that had no free space. Any thing that needs a little working room on the hard disk should ether have it reserved or know how to use ram.

So what was the problem? Simple Backup Config. Even though I told it to use an external disk it still backed-up to /var/backup. Simple backup Config should know better then to fill your root partition full, or even to use it for backup.

PS File Backup Manager is also on my list of programs to avoid, because it will not restore from a backup that it made that has a space it its name, and it does not let the user choose were to restore to.

---

### Post by coffeecat on 2011-11-25
Closed for necromancy.

---

