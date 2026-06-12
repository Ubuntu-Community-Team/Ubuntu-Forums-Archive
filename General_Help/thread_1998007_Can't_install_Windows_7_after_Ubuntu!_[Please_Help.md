---
title: "Can't install Windows 7 after Ubuntu! [Please Help]"
date: 2012-06-06
forum: General Help
---

### Post by Anilyst on 2012-06-06
I installed ubuntu to test it out and because I needed to use my pc till I could get Windows 7 (have it on usb, installed on it) but now whenever I go to boot from usb and go to install windows 7 when I get to the point where I choose the partition it says "Setup unable to find partition" or something along those lines (Pc is off at the moment), I've looked up SOOO many things on the internet about this issue but just can't seem to fix it. HELP IS GREATLY APPRECIATED!!!

---

### Post by carl4926 on 2012-06-06
Windows need a primary partition in ntfs or fat format to place it's boot code, do you have that?

---

### Post by Anilyst on 2012-06-06
> **carl4926 said:**
> Windows need a primary partition in ntfs or fat format to place it's boot code, do you have that?
 
 
How can I make that?

---

### Post by carl4926 on 2012-06-06
Boot in to Ubuntu or use a Ubuntu Live CD

Open a terminal and post the putput of

```
sudo fdisk -l
```From that we can see what you have. It's likely you may have to re-install, but lets see first

---

### Post by ysNoi on 2012-06-06
hi Anilyst...

If you plan to dual boot your system (ubuntu & windows), it would be easier to install first Windows then Ubuntu afterwards... Just make sure you have a separate partition to be used for Ubuntu... :)

---

### Post by Anilyst on 2012-06-06
> **carl4926 said:**
> Boot in to Ubuntu or use a Ubuntu Live CD
 
Open a terminal and post the putput of
 
```
sudo fdisk -l
```From that we can see what you have. It's likely you may have to re-install, but lets see first
 
Hm, Currently I don't have an operating system because I tried to install windows 7, So shall I reinstall Ubuntu?

---

### Post by carl4926 on 2012-06-06
You could install Ubuntu, but it'd be better to install windows first

Use an ububut live cd and start gparted and do this

sda1 ntfs for windows
swap
extended
ext4 for /
ext4 for /home

Install windows to sda
get it fully updated, takes forever.......

Install Ubuntu

---

### Post by Anilyst on 2012-06-06
> **carl4926 said:**
> You could install Ubuntu, but it'd be better to install windows first
 
Use an ububut live cd and start gparted and do this
 
sda1 ntfs for windows
swap
extended
ext4 for /
ext4 for /home
 
Install windows to sda
get it fully updated, takes forever.......
 
Install Ubuntu
 
Redownloading ubuntu should be done in a few minutes, Then I'll install to usb and boot from the usb.
 
Edit: Update; Download complete, Installing to USB.

---

### Post by Anilyst on 2012-06-06
I'm not trying to dual boot (My hdd isn't large enough to do that well) and so I figured all I would need to do is make the hdd ntfs which after I went and installed win7 on usb it STILL didn't work, I don't know maybe I'm just doing this wrong. N
ow I'm installing ubuntu onto my usb once AGAIN. This is really beginning to **** me off.

---

### Post by carl4926 on 2012-06-06
We need to see

```
sudo fdisk -l
```

---

### Post by Anilyst on 2012-06-06
> **carl4926 said:**
> We need to see

```
sudo fdisk -l
```
  

Alright I ran ubuntu off usb and used that command in the terminal and it came up with:

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b08bfbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   312496127   156247040    6  FAT16

Disk /dev/sdb: 8036 MB, 8036285952 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

```

---

### Post by Mark Phelps on 2012-06-06
> **Anilyst said:**
> ...after I went and installed win7 on usb it STILL didn't work...

If you mean you tried to install win7 TO USB -- that will not work.  MS doesn't want folks walking around with "portable" versions of Win7.  Win7 can only be installed to a hard drive (or SSD).

If you meant you installed Win7 FROM USB, to your hard drive, and that is not working -- then you need to post in a Windows 7 forum  to get detailed answers.  Recommend sevenforums.com

---

### Post by Anilyst on 2012-06-06
> **Mark Phelps said:**
> If you mean you tried to install win7 TO USB -- that will not work. MS doesn't want folks walking around with "portable" versions of Win7. Win7 can only be installed to a hard drive (or SSD).
 
If you meant you installed Win7 FROM USB, to your hard drive, and that is not working -- then you need to post in a Windows 7 forum to get detailed answers. Recommend sevenforums.com
 
pendrivelinux has an option for Windows 7, I have it 'installed' to the usb to where when I boot from my usb it loads to the installer and it does work because I've used it before.
 
This is really, really, really aggrivating. -.-"

---

### Post by Anilyst on 2012-06-06
Thank god, I figured it out (I think) It was because I was installing via a usb and I suppose it was confusing the installation manager. I burned a cd from the information on the usb and it got pass the hard drive selection part BUT I guess because I burned it with the fastest possible settings It missed a file so I'm reburning it on the lowest possible speed. We shall see

---

### Post by Kr0nZ on 2012-06-06
> **Anilyst said:**
> Thank god, I figured it out (I think) It was because I was installing via a usb and I suppose it was confusing the installation manager.

Did your usb have multiple partitions?
I install win 7 via USB all the time. But once I was trying to make a multi-partition/multi-boot usb, and whenever I tried booting win7 setup from a non 1st partition I would get the "Setup unable to find partition" message.

---

### Post by Anilyst on 2012-06-06
> **Kr0nZ said:**
> Did your usb have multiple partitions?
I install win 7 via USB all the time. But once I was trying to make a multi-partition/multi-boot usb, and whenever I tried booting win7 setup from a non 1st partition I would get the "Setup unable to find partition" message.
 I don't think so but Windows 7 is now installed. it worked. YAY

---

