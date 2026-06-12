---
title: "USB not automounting"
date: 2012-07-24
forum: General Help
---

### Post by Ububtubobl on 2012-07-24
The documentation says to run "[B]dconf-editor" in terminal to set-up automounting, but the command dose not  exist according to Terminal. I have 10.4 installed . The system recognizes all the usb ports but will not mount flash memory  or external usb drives. Can anyone suggest something . Thanks.

Documentation is probably wrong and meant "gconfig-editor".

Automounting is checked but drives are not mounting. Any ideas what may be the problem?

[/B]

---

### Post by dino99 on 2012-07-24
check that usbmount is installed

[http://ubuntuforums.org/showthread.php?t=1438364](http://ubuntuforums.org/showthread.php?t=1438364)

---

### Post by Ububtubobl on 2012-07-24
> **dino99 said:**
> check that usbmount is installed

[http://ubuntuforums.org/showthread.php?t=1438364](http://ubuntuforums.org/showthread.php?t=1438364)
I see no reference to "usbmount" in  Apps/nautilus/preferences,  only "media" and automount is checked.

---

### Post by teward on 2012-07-24
What I think that dino99 meant was check via Synaptic or software center, or command-line tools to see if the package `usbmount` is installed...

---

### Post by Ububtubobl on 2012-07-24
Software Centre says it is installed.

---

### Post by NikTh on 2012-07-24
Hi , 
try these commands 
```

gsettings set org.gnome.desktop.media-handling automount "true"
gsettings set org.gnome.desktop.media-handling automount-open "true"
```
Did they work ?

Thanks

---

### Post by Ububtubobl on 2012-07-25
Both commands are marked "true".

---

### Post by NikTh on 2012-07-25
Hi , 
after a little search I think I found something .. 
run this in terminal ```

sudo modprobe -r floppy
``` 
and restart your pc. 

Thanks

---

### Post by Ububtubobl on 2012-07-25
Thanks for your help. The floppy is no longer showing in Disk Utility, but neither is the USB. I guess the floppy was not the problem. (This machine still has one.)

P.S. I had not rebooted when I made the above reply. After a reboot the A drive is back but still no usb mounted.

---

### Post by NikTh on 2012-07-25
Hi , 
take a look at this thread -- > [http://ubuntuforums.org/showthread.php?t=1470705](http://ubuntuforums.org/showthread.php?t=1470705)
you said that you have Ubuntu 10.04 

Thanks

---

### Post by Ububtubobl on 2012-07-25
Thanks. Hal is installed, floppy drive is present. I un-installed "usbmount" (pmount is installed) and I reversed that process. The usb icon dose not show up in places/computer or on the desk top or in disk utility under administration. It was working till a few days ago. I am not aware that I changed anything. Could this have been caused by a software update?

---

### Post by NikTh on 2012-07-25
> **Ububtubobl said:**
>  I am not aware that I changed anything. Could this have been caused by a software update?

Hi , 
this is possible yes. 
Do you have an older kernel installed to boot from ? 
Try to disable Floppy from Bios config. page

Thanks

---

### Post by Ububtubobl on 2012-07-26
I did disable the adrive in the bios to no effect. My system has a working floppy so that's not the problem. Would reinstalling the kernel help?

---

### Post by Ububtubobl on 2012-07-26
I saved reports suggested in  troubleshooting mount devices. The are not helpful to me. Would someone more knowledgeable take a look at them for me. 
Thanks.

[sudo] password for robert: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x259d4594

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19717   158375546+   7  HPFS/NTFS
/dev/sda2           19717       38914   154194945    5  Extended
/dev/sda5           19717       38165   148183040   83  Linux
/dev/sda6           38165       38914     6010880   82  Linux swap / Solaris
robert@robert-desktop:~$ 
---------------------------------------------------------------------------------------------------------------------robert@robert-desktop:~$ sudo blkid
/dev/sda1: UUID="D414256714254DB4" TYPE="ntfs" 
/dev/sda5: UUID="940e41f9-ffb0-4f43-9321-77012f7f1dc9" TYPE="ext4" 
/dev/sda6: UUID="56be612c-7689-469d-ada2-829a7f1cf09e" TYPE="swap" 
robert@robert-desktop:~$ 

----------------------------------------------------------------------------------------------------------------------- physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WMAV2DA99428
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=259d4594
  *-cdrom
       description: DVD writer
       product: DVD-RW_GSA-H11N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JH02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
robert@robert-desktop:~$ 
---------------------------------------------------------------------------------------------------------------------------
robert@robert-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=940e41f9-ffb0-4f43-9321-77012f7f1dc9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=56be612c-7689-469d-ada2-829a7f1cf09e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
robert@robert-desktop:~$ 
-------------------------------------------------------------------------------------------------------------------------

---

### Post by NikTh on 2012-07-26
Hi , 
do you use this floppy drive ? 
can you remove this line from /etc/fstab ? 
> ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```**But its better no remove.. its better to add a # symbol at start . **
So open /etc/fstab like this 
```
gksudo gedit /etc/fstab
```and make the line like this
```
**#**/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```save the file and restart PC. 
Thanks

---

### Post by Ububtubobl on 2012-07-26
Thanks for your input. I did as you suggested and checked that the change was made. ( the USB not mounting though)

---

### Post by Ububtubobl on 2012-07-26
Is it possible to reinstall ubuntu without overwriting the home folder?

Perhaps the solution will be to reinstall Ubuntu but without the use of external usb h.d, I won't be able to back up my home folder. Deja Dupe doesn't appear to span dvd's with  a large file. Any suggestions?

---

### Post by NikTh on 2012-07-26
> **Ububtubobl said:**
> Is it possible to reinstall ubuntu without overwriting the home folder?

Hi , 
yes you can reinstall without overwriting home folder , IF you have /home folder separate from root. Do you ? 
I think you don't have , cause i see in /etc/fstab only ONE entry with root. The other is swap and the other is floppy. No separate /home. 

So you must first backup /home directory to an external HDD (or usb if its short) and then you can proceed to a fresh installation of Ubuntu 10.04.4 

You can easily copy your /home directory with rsync command. 
First gather all your important files to ONE folder (create a new) so they are all gathered to one folder. 
Then use rsync like this.. 
```
rsync -avS /target_directory /destination_directory
```Check out if all files transfered correctly . 
You can use the same command to transfer again the files from external HDD to your new /home .
Sorry that you must reinstall Ubuntu to solve this problem. 
A suggestion might be to wait a little long ,  because this problem does not affect the functionality of system-wide , maybe someone has a solution for this so you can avoid fresh install.

Thanks

---

### Post by Ububtubobl on 2012-07-27
I was unable to backup to external hard drive because my usb drives won't mount (my original problem)  so I added a partition to my HDD with Gparted and backed up onto it. With a fresh install my USB did mount but when I reinstalled the home folder I reinstalled the problem. I guess I will do a more selective backup and try again. NikTh thanks for all your help.

---

### Post by Ububtubobl on 2012-07-27
More to report. After several reinstalls of 10.04 today with and without updating I have discovered the following--The usb automounts once. After manually unmounting, it will not auto-mount even after rebooting. If I insert the thumb-drive into the port at the Grub screen before Ubuntu loads, it mounts.

---

### Post by Ububtubobl on 2012-08-02
Automount loads a Flash or USB drive only once after a fresh install of 10.04. I get the same result using a live CD. (even with 12.04.) Once it has been unmounted the drive will not mount again. By booting from the HDD with the USB drive plugged in at start-up, it mounts but only with Root privileges. This started a couple of weeks ago. I followed the suggestions from the documentation, but so far no results. This computer dual boots to XP and the Drive is plug and play there so I don't think it is a hardware problem. Any more suggestions?:confused:

---

