---
title: "problems starting ubuntu 10.4"
date: 2011-05-23
forum: General Help
---

### Post by kowalsky on 2011-05-23
hi all,
something happened to my ubuntu 10.4 - I can't see my desktop after boot. As a matter of fact, when I boot I see a message saying: Continue to wait; or press S to skip mounting, or M for manual recovery. I left it like that over night, this morning I found the logon box, typed my password and I got to an empty desktop.
I did a Ctrl-Alt-F1 and logged on there, I am looking at /etc.fstab and I see the first lines like this:
proc /proc proc nodev,noexec,nosuid 0 0 
# / was on /dev/sda3 during installation UUID=3538bcd0d-...
ext4 errors=remount-ro 0 1

I guess something is wrong right from the start, some portion of the file system is not recognized anymore (or is in the wrong place) ... 
Is there any chance I can fix this?
What do I do next?
Thank you very much,
kowalsky

---

### Post by 3Miro on 2011-05-23
Please post the entire fstab file (the small part looks OK). Also, please post the output of:

```
ls -al /dev/disk/by-uuid/
```
and
```
sudo fdisk -l
```

Those two commands would tell us your hard-drive layout.


Here is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cde8aec5-475e-4e9c-9a4b-89a9d051ba68 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c4c40a3-2374-4696-9697-d135038e29bd none            swap    sw              0       0

```

---

### Post by kowalsky on 2011-05-23
thanks 3Miro,
my fstab is as follows (in its entirety):
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=3438bd0c-0d22-4164-afcf-ee0b66fe86cd /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation UUID=ea6815ce-faad-433c-bf80-822c1d724139 /boot ext4 defaults 0 2
/dev/sdb1 /home/ ext4 defaults 0 2
# swap was on /dev/sda2 during installation
UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 /swap ext4 defaults 0 2
#tmp was on /dev/sda6 during installation
UUID=3a92c67c-6e2c-4e53-a9d7-18de40817243 /tmp ext4 defaults 0 2
# /usr was on /dev/sda7 during installation UUID=fa81ccc4-f52a-4975-8695-5de17e5db63b /usr ext4 defaults 0 2
# /var was on /dev/sda5 during installation UUID=0e7aa55e-da0f-4ecb-af46-f9312cec57fd /var  ext4 defaults 0 2

and results for ls -al /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 160 2011-05-22 23:29 .
drwxr-xr-x 5 root root 160 2011-05-22 23:29 ..
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 0e7aa55e-da0f-4ecb-af46-f9312cec57fd -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 3438bd0c-0d22-4164-afcf-ee0b66fe86cd -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 3a92c67c-6e2c-4e53-a9d7-18de40817243 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 b09ba97e-7b75-4083-bd66-a235a67d2220 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 ea6815ce-faad-433c-bf80-822c1d724139 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-05-22 23:29 fa81ccc4-f52a-4975-8695-5de17e5db63b -> ../../sda7

Thank you very much,
waiting for the next step,
kowalsky

---

### Post by 3Miro on 2011-05-23
> **kowalsky said:**
> 
# swap was on /dev/sda2 during installation
UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 /swap ext4 defaults 0 2


Did you change that? The swap line should look like:

```
UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 none swap sw 0 2
```

Swap doesn't have a mount point and it is a separate file system (not ext4). Also, defaults apply for ext* only.

Make a backup of the old fstab file and try to edit the existing one:

Backup
```
sudo cp /etc/fstab /etc/fstab_backup
```

To edit
```
sudo nano /etc/fstab
```
or if you prefer graphics:
```
gksudo gedit /etc/fstab
```

---

### Post by kowalsky on 2011-05-23
I did not change anything, the results of the two commands were exactly what the system reported.
I went in now, though and changed the entry for swap, did a sudo reboot and I am getting the same Continue to wait ...

I pressed s to skip mounting and I get two error messages:
Could not update ICEauthority file /home/vv/.ICEauthority, clicked Close to close the error box, then a second error message: There is a problem with the configuration server.(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256) clicked Close to close this message box as well (then there's an error from Nautilus not being able to create some file in my /home/vv directory). I am now again in the GUI with an empty, empty desktop. 

Ctrl+Alt+F1, log on , cat /etc/fstab gives me:
# /swap was on /dev/sda2 during installation
UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 none swap sw 0 2

What next :-( ?
thanks,
kowalsky

---

### Post by 3Miro on 2011-05-23
Can you post the result of:

```
sudo fdisk -l
```

---

### Post by kowalsky on 2011-05-23
sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units=cylinders of 16065*512=8225280 bytes
Sector size(logical/physical):512 bytes/512 bytes
I/O size(minimum/optimal):512 bytes/512 bytes
Disk identifier: 0x0001592f

Device    Boot  Start    End   Blocks   Id   System
/dev/sda1 *         1     13    98304   83   Linux Partition 1 does not end on cylinder boundary.
/dev/sda2          13     75   500736   83   Linux Partition 2 does not end on cylinder boundary.
/dev/sda3          75    573  4001792   83   Linux Partition 3 does not end on cylinder boundary.
/dev/sda4         574  60802 483782657   5   Extended
/dev/sda5         574   1072   4000768  83   Linux
/dev/sda6        1072   2192   9000960  83   Linux
/dev/sda7        2192  60802 470778880  83   Linux

Thanks,
kowalsky
By the way, I lost all my linux skills a long time ago, what I see does make sense (vaguely), however I can't tell anything is wrong ... maybe when we're done I will be able to remember some basic stuff.
Anyway, thanks a bunch again!

---

### Post by 3Miro on 2011-05-23
First of all, you don't have a swap partition. Here is what my thing looks like. All of your partitions are ext4 (maybe ext3).

```
/dev/sda1              63    16771859     8385898+  82  Linux swap / Solaris
/dev/sda2        16771860    79682399    31455270   83  Linux
/dev/sda3        79682400   913858559   417088080   83  Linux
/dev/sda4   *   913858560   976773119    31457280   83  Linux

```

This means that the swap line in the file doesn't make much sense (none swap sw will not work for an ext4 partition). You can revert the changes to /swap again (even though I don't know what you would have in /swap).

On your install, do you remember which partition you listed as what. Which partition was set for /, which one for /home and so on?

Also, post the fstab file again, but then use the code tags (the # symbol on the editor for the forum messages). The Code tags make things appear nice, otherwise we may lose some of the new lines and such.

---

### Post by kowalsky on 2011-05-23
3Miro, thanks!
I found some notes:
```

/dev/sda
/dev/sda1 /boot primary 100MB ext4
          /swap primary 512MB
          /     primary 4097MB
          /var  logical 4096MB
          /tmp  logical 9216MB

/dev/sdb
dev/sdb1 /home 707007MB

```    

I can't see any sdb in results from fdisk -l ...

I reverted to the initial fstab; the result to cat /etc/fstab is:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda3 during installation UUID=3438bd0c-0d22-4164-afcf-ee0b66fe86cd / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation UUID=ea6815ce-faad-433c-bf80-822c1d724139 /boot ext4 defaults 0 2
/dev/sdb1 /home ext4 defaults 0 2
# swap was on /dev/sda2 during installation UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 /swap ext4 defaults 0 2
#tmp was on /dev/sda6 during installation UUID=3a92c67c-6e2c-4e53-a9d7-18de40817243 /tmp ext4 defaults 0 2
# /usr was on /dev/sda7 during installation UUID=fa81ccc4-f52a-4975-8695-5de17e5db63b /usr ext4 defaults 0 2
# /var was on /dev/sda5 during installation UUID=0e7aa55e-da0f-4ecb-af46-f9312cec57fd /var ext4 defaults 0 2

```

This is it ... I am using a windows machine for posting these messages, I am typing everything I see on the Linux machine - I am checking everything twice before I post ... hopefully the formatting is OK now, too.
Thanks,
kowalsky

---

### Post by 3Miro on 2011-05-23
The swap issue is an issue, but we will solve that later. The sdb issue is a big one.

How many hard-drives does your computer have? sda is the first HDD. sda1 is the first partition on the first HDD. sda3 is the third partition on the first HDD. sdb1 is the first partition on the second HDD.

dev/sdb1 /home means that your home folder along with all of your personal files (settings, Documents, Downloads ...) in it situated on the second HDD. And the second HDD does not show on /etc/fstab.

If you have only one HDD and you have never had another, then your info is incorrect. How are you getting the output of the commands that I gave you, can you boot into the system at all. If so, can you post the output of:
```
ls /home/
```
(list everything in /home, if you never had a second HDD, then you should see a folder with your username)

---

### Post by 3Miro on 2011-05-23
I read the fstab carefully and it is totally broken:

If you edit the file, note that Windows and Unix use different ways to denote end of line. You should edit the Linux settings files only with a Linux editor (you can use "nano" for terminal and "gedit" for graphics). Something like:

```
sudo nano /etc/fstab
```

This is what the fstab file should look like. Note the new lines that I added. Any line starting with # is just being ignored. Lines should start with a device identifier by either UUID or /dev/sd...

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda3 during installation 
UUID=3438bd0c-0d22-4164-afcf-ee0b66fe86cd / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation 
UUID=ea6815ce-faad-433c-bf80-822c1d724139 /boot ext4 defaults 0 2
/dev/sdb1 /home ext4 defaults 0 2
# swap was on /dev/sda2 during installation 
UUID=b09ba97e-7b75-4083-bd66-a235a67d2220 /swap ext4 defaults 0 2
#tmp was on /dev/sda6 during installation 
UUID=3a92c67c-6e2c-4e53-a9d7-18de40817243 /tmp ext4 defaults 0 2
# /usr was on /dev/sda7 during installation 
UUID=fa81ccc4-f52a-4975-8695-5de17e5db63b /usr ext4 defaults 0 2
# /var was on /dev/sda5 during installation 
UUID=0e7aa55e-da0f-4ecb-af46-f9312cec57fd /var ext4 defaults 0 2
```

---

### Post by kowalsky on 2011-05-23
3Miro,
I know I have 2 hard drives, and you are correct: my /home should be on the second hard drive, the one we're not seeing at all.

I can boot in my Linux machine, I executed all commands on it, I posted the results - the only change I made was to modify the swap entry in the /etc/fstab, then I reverted by cp /etc/fstab_backup /etc/fstab. All editing was done with nano on the Linux machine.

I got the lines with UUID ... on the same line with the comments while typing this in the post, however, if I look on my Linux now, I see the fstab is exactly as you recomended.

I guess I have a big problem with my 500 GB second drive. Is it possible to recover the data on it?

Thanks,
kowalsky

---

### Post by 3Miro on 2011-05-23
So we found the problem then. Your second HDD is not detected by the system.

There a couple of things that you can try. First, make sure the BIOS can actually see the HDD (and that the HDD is properly connected).

Second, you can try to boot from a LiveCD or LiveUSB (i.e. get an Ubuntu CD or USB, boot and say "Try Ubuntu"). From there, you can use the file manager (nautilus) to read the HDD and hopefully get the data from it.

You can also try to boot with an older version of your kernel. When you boot initially, there should be a list of possible kernels and safemodes (if  you don't see a list, hold down the Enter key on boot).

---

### Post by kowalsky on 2011-05-23
thank you very much,
i will try the CD I used to install my ubuntu 10.4, I should have one copy left somewhere ... 

I would like to flag this thread as solved (since for all practical purposed it is solved), but I can't find the way to do this ... 

Anyway, 
Thank you again,
kowalsky

---

### Post by 3Miro on 2011-05-23
Let me note something on the swap thing. Right now you have a partition called swap, but it is not used as "swap". Swap is when the OS runs out of RAM and uses the HDD for extra space.

To make a swap partition, use Gparted either from within working Ubuntu installation or from a LiveCD/LiveUSB. Make sure you don't have anything important on the swap partition and then reformat it into Linux Swap.

Then you need to change the fstab file to the 
```
UUID=*** none swap sw 0 2
```

replace the *** with the UUID from the new partition, formating changes the UUID. You can find the UUID by using:
```
ls /dev/disk/by-uuid
```

---

