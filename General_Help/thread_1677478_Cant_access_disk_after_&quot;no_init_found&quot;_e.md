---
title: "Cant access disk after &quot;no init found&quot; error"
date: 2011-01-28
forum: General Help
---

### Post by perfecti0n on 2011-01-28
Hello!

I have a HP ProBook 6540b labtop and while doing a system resume ubuntu  froye at splash screen with the dots. So I powered it off and when  starting it again the error showed up

```
mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)
```Anyway after some googling for the solution i found a tip to do this

sudo fdisk -l

where i got the partition where linux is installed 
and then

sudo fsck /dev/sda1

however, doing this...the terminal returns

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```I  cant access the disk through Nautilus either. There i get Unable  to  mount 488GB filesystem. DBus error  org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already  pending

So can anyone explain to me what the heck is going on with my harddrive?  is it dead? is there anyway to recover the data? will a reinstall of  ubuntu fix the issue?

////////////////////// Can mods please delete my other thread in labtop-hardware cat.

---

### Post by Rubi1200 on 2011-01-29
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Also, while on the LiveCD run this command and post the output:

```
sudo lsof | grep sda1
```

---

### Post by perfecti0n on 2011-01-29
The script has been stuckfor 20 minutes at  "Searching /dev/sda1 for information...". Is that normal?


EDIT: I used slax usb boot and then ran fsck and it works now :D (apparently the problem is that ubuntu wants to auto-mount the drive :D
i'm just glad all my data is still here hehe. Thanks for your help anyway, really appreciate it!

---

### Post by Rubi1200 on 2011-01-29
Actually, Slax would have been my next suggestion. I helped some people recently with similar issues and Slax got the job done.

Glad you got it sorted out now :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by Ticatla on 2011-02-01
Ok, I have exactly the same problem. Searching sda1 for information is taking for ever.I tried booting with slax but the screen freezes after a while... hum. Lost.

---

