---
title: "Mount: mounting /dev/disk Failed:"
date: 2011-03-09
forum: General Help
---

### Post by HxCbandanna on 2011-03-09
I really have no idea what happened, or what I need to do to fix this. I am a pretty basic user with a little computer competency but I really don't know what I am dealing with here.

I turned on my computer. 
It runs through BIOS.
A new screen appears.
It is titled GNU GRUB version 1.98+20100804-5ubuntu-3
and there is a list of options, the first highlighted option is this: Ubuntu, with linux 2.6.35-22-generic
I press enter.
Within a few seconds this appears on my screen:

Mount: Mounting /dev/disk/by uuid/abee1200-526a-4f64-bbf3-3a5b126839f9 on /root
Failed: Invalid argument
Mount: Mounting /dev on /root/dev failed: No such file or directory
Mount: Mounting /sys on /root/dev failed: No such file or directory
Mount: mounting /proc on /root/dev failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init=bootarg

Busybox  v1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)
Enter 'help' for a list of built in commands.

(intramfs)_




And from this point I have no idea as to what to do.
Please help if you can, its greatly appreciated.

---

### Post by psusi on 2011-03-09
Type "dmesg" at the prompt.  There should be some more detailed error messages near the end of the output.  My guess is that your filesystem is corrupt or the disk is damaged.  Boot from the livecd, go into the disk utility and check the drive's SMART status.  Make sure there aren't any reallocated, pending, or offline_uncorrectable sectors, and check the filesystem.

---

### Post by _mOrgoth_ on 2011-03-09
Your filesystem is corrupt! I think that you can not approach to partition with livecd. I will say that it is already mounted.. I resolved same problem like this..
1. download and boot systemrescuecd
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
2. boot from it
3. go into graphical environment:
chose: standard 32bit kernel (rescuecd)......, and than chose graphical environment..
If your screen shots down than reboot and chose vesa..
4. when started under systen start gparted
5. find your partition..(in my case was sdb2..)
6. click on it, right click and chose check..

Than it will try to fix your filesystem.. It resolved for me and now I boot normally.
This is my thread:
[http://ubuntuforums.org/showthread.php?t=1702650](http://ubuntuforums.org/showthread.php?t=1702650)

---

### Post by HxCbandanna on 2011-03-16
Thank you guys for the help. I haven't messed with my comp in a few days because I've been busy. I will be sure to post the results.

---

### Post by HxCbandanna on 2011-03-17
I downloaded the systemrescuecd-x86-2.0.1
then the Sysresccd-installer-1.1.2

I used sysrescd-installer to burn the iso onto my USB.

Initially I had problems booting from the USB iso using the sysresccd installer. I would get a prompt saying "Operating System Missing"

I then downloaded linux live USB creator and used that program to burn the iso onto my USB.

I rebooted and I no longer got the missing operating system prompt.
Instead, the iso ran through and eventually opened up the user interface. ( I never had to choose the vesa option either )

I then clicked the gparted icon in the lower left corner,
selected my main partition, then I right clicked it and selected "check".

Once I ran the gparted check it took a few minutes of waiting, then it said the partition was checked and repaired succesfully.

I shut down my computer and was able to boot into linux successfully. 

Thank you for the help and instructions. ):P

---

