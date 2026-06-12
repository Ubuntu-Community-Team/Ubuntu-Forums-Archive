---
title: "sytem recovery"
date: 2010-11-13
forum: General Help
---

### Post by liddlem on 2010-11-13
A while back, I installed Ubuntu10.04 - All worked fine till my son decided to install a game.
Now the system doesn't even boot up.

I thought I would simply copy all my "important" files to USB and then reload the OS.
So I loaded the "Try Ubuntu" disk with the intention of mounting the HDD.

The problem is that when I mount the HDD, I see only 2 folders (GRUB and LOST + FOUND) and a number of files (abi-blah-generic, initrd.blah and System.blah)  - But I cannot see the HOME folder where (I presume) all my stuff is.

I tried to "Recover a broken system" but got as far as a terminal window - then I am LOST! 
(I'm a Windows junkie trying to reform to Ubuntu)

Any tips, ideas or tricks would be helpful.
Thanks.

---

### Post by Hippytaff on 2010-11-13
I feel your pain...got two kids who mess about with things....if you can post the results,txt of this scrip
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
some people who are far more versed in the way of the ubuntu migh be able to help

---

### Post by drs305 on 2010-11-13
Did you have a separate /boot partition? It sounds like you are looking only at the contents of a /boot partition.

From the LiveCD, run the following command, which should show you all the partitions the system is seeing. Once you find /home (or whatever you are looking for, mount it and open a browswer to inspect the contents).

```
sudo blkid
sudo mount /dev/sdXY /mnt  (example: sudo mount /dev/sda6)
nautilus /mnt

```

---

### Post by liddlem on 2010-11-13
Ok . . . . ? Didnt think I'd get a response quite so quickly. Thanks for the input.

I have tried both suggestions. Please see attached files.

RESULTS.txt is the result of HIPPYTAFF's suggestion.

The MountInfo.png is a screenshot of what I can see both before and after running drs305's script. 
(I.E. This is exactly what I see, whether I mount the drive manually myself, or if I use your script.) - Still cannot see the HOME folder though.

Thanks

---

### Post by zaphod777 on 2010-11-14
> **liddlem said:**
> Ok . . . . ? Didnt think I'd get a response quite so quickly. Thanks for the input.

I have tried both suggestions. Please see attached files.

RESULTS.txt is the result of HIPPYTAFF's suggestion.

The MountInfo.png is a screenshot of what I can see both before and after running drs305's script. 
(I.E. This is exactly what I see, whether I mount the drive manually myself, or if I use your script.) - Still cannot see the HOME folder though.

Thanks

hmm I'm not sure I can be much help but I think the problem is you are using LVM HDD encryption on the whole drive. Only the boot portion is not encrypted but everything else is. 

I am not sure how to recover from there. It might be easier to troubleshoot the boot problem (for me since I have no idea otherwise others may no better than me). 

What do you see when it fails to boot? Also when you see the Ubuntu screen press ESC to see more meaningful messages.

---

### Post by liddlem on 2010-11-14
Thanks zapphod777.
when booting from HDD, I get the purple background, but no application / nav bar. (At the top and bottom of the screen respectively)
I do get a terminal window, which opens by default, in my home folder.
But I have no idea how to mount my USB drive or how to start the app bars so that I can save my files.

---

### Post by zaphod777 on 2010-11-14
> **liddlem said:**
> Thanks zapphod777.
when booting from HDD, I get the purple background, but no application / nav bar. (At the top and bottom of the screen respectively)
I do get a terminal window, which opens by default, in my home folder.
But I have no idea how to mount my USB drive or how to start the app bars so that I can save my files.
Great!  You are in good shape.  I am out right now but I will post details on what to do when I get home.

---

### Post by zaphod777 on 2010-11-14
when you are logged in run "df -h" and write down the devices you see.

Then connect the USB drive and run "df -h" again and write down where the new drive is mounted. 
Then run this command the mountpoint id is where the USB drive is mounted. 
```
sudo cp -v -R * /mountpount
```

if it doesn't show up in the mount list run
```
dmesg|tail
```

then write down the usb device that was connected something like "/dev/sdb1"
then we need to create the mount point

```
sudo mkdir /media/usb

```

then you need to mount it
```
sudo mount /dev/sdb1 /media/usb
```

Then to copy all of your files to the USB drive but first make a backup folder on the USB drive.
```
sudo mkdir /media/usb/backup
sudo cp -v -R * /media/usb/backup

```

once it is done copying make sure you unmount the USB drive cleanly before disconnecting it.
```
sudo umount /media/usb
```

Also a note about the file system on the USB drive. If it is FAT32 then the biggest file you can copy is 4GB if you have files bigger than that then you need to make sure the drive is formated in EXT3, EXT4, or NTFS.

There is are also a lot of different options for the copy command to see them all just run 
```
man cp
```

---

### Post by zaphod777 on 2010-11-16
Did it work?

---

### Post by liddlem on 2010-11-20
Sorry Zaphod
Only JUST got back to looking at this machine. 

i am trying to manage a 158 workstation / 8 server site and am planning an upgrade to 1gb wireless backbone for an additional 120 machines for implementation early January. Doing this on my own at the moment so have been overworked and underpaid - as usual.

Will try it in a few minutes and let you know how it goes.

Thanks.

P.S. - the site is purely Windows, but I am SERIOUSLY considering a  move to Ubuntu. The problem is finding time to learn and test.

---

