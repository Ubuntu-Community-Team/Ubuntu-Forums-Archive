---
title: "error loading operating system please help?"
date: 2010-02-09
forum: General Help
---

### Post by ontherooftop on 2010-02-09
I wanted to install XP and did many commands looking at google to 
install xp on a second partition and I tried to use grub, but it
didn't work for me, then I tried Lilo with all the commands givin
also didn't work. So I used a ubuntu live CD and used Gparted to 
remove the windows partition and set the Ubuntu which is on dev/sda1
ext4 to boot. Now it says error loading operating system when i restart,
I have all my important files on there, how can I boot back in ubuntu,
or how can I get my files back because I can't open them on the Live CD?

---

### Post by Joe Ker1086 on 2010-02-09
is it error 15 - could not locate file???

---

### Post by ontherooftop on 2010-02-09
Hold on Im on a live CD now, I tried these commands from someone 
and I will try and see if I can boot back and tell the results. 
I just did this on a live CD.

) root@ubuntu:/home/ubuntu# fsck.ext4 -f /dev/sda1

(...found many errors. <y> to all...)

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 135285/15081472 files (0.4% non-contiguous), 3525756/60314026 blocksProblem found and fixed!

2) root@ubuntu:/home/ubuntu# fsck.ext4 -f /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 135285/15081472 files (0.4% non-contiguous), 3525756/60314026 blocksDouble checked. Yes, it's really fixed!!!

3) root@ubuntu:/home/ubuntu# sudo fsck.ext4 -p /dev/sda1
/dev/sda1: clean, 135285/15081472 files, 3525756/60314026 blocks]IDK what this one did, but someone told me to do that... lol

---

### Post by Joe Ker1086 on 2010-02-09
that fix ur problem?

---

### Post by ontherooftop on 2010-02-09
Nope again when I boot all it says is ERROR loading operating system.

Is there a fix, or a way I can get in to the hard drive to get my
files because I have like 8 gigs of info and things that I really
need and I can't access them or boot into the operating system.

---

### Post by ontherooftop on 2010-02-09
my ubuntu partition is on dev/sda1  ext4

---

### Post by ontherooftop on 2010-02-09
also I have /dev/sda3 extended
and /dev/sda5  Linux swap if that helps , Im still

kind of a noob I think I really messed things up with all
the commands I did for grub and then Lilo. I think I might
have even deleted grub or seriously damaged it.

---

### Post by Joe Ker1086 on 2010-02-09
If that is the exact error then Im not exactly sure what the fix is.... i know that you can get the info off of there but your gunna need a live cd and a usbstick..... (im sure there are other ways but this is the way i know)

when you have a usb stick and live cd goin do

```
fdisk -l
```

and post the output. That way we can copy everything from that drive to the usb stick....or if you have a portable hd you could use that...

---

### Post by ontherooftop on 2010-02-09
I am on a live CD right now, i just did this command and got the
error 15 could not locate file.

grub> find /boot/grub/stage1

Error 15: File not found

---

### Post by ontherooftop on 2010-02-09
here is what I got with the command you gave me and thanks for helping me out. apreciate it.

ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    b  W95 FAT32

---

### Post by Joe Ker1086 on 2010-02-09
ok, you could try to reinstall grub.... [http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html](http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html)

kinda tricky depending on level of experience... or you could copy over your files to the usb stick... which would you prefer?

---

### Post by ontherooftop on 2010-02-09
can you help me copy files to the USB, I have only a 4 gig USB drive
so I need to select with folder and files I want because there is 12
gigs of space used.

---

### Post by Joe Ker1086 on 2010-02-09
ok, first you have to mount the partition with the files on it to copy over and the usb stick (usb stick should be sdb1)

so make a directory in /mnt for each

mkdir /mnt/usbstick
mkdir /mnt/harddrive

then do the mount

mount /dev/sdb1 /mnt/usbstick
mount /dev/sda1 /mnt/harddrive  (i think you said this is where your files are right?)

ok then do a 

ls /mnt/harddrive

this will show you all the folders within this directory

---

### Post by Joe Ker1086 on 2010-02-09
Im leaving work now so i dont know if i will be back on until tomorrow or late tonight...... IM me at JoeKer1086 if you are on aim and it will go to my phone..send a message even if i am not showing online and it should alert me...

---

### Post by ontherooftop on 2010-02-09
Ok so far I did the commands and now it shows whats on my hardrive,
the folder is home where my files I want to put on the stick, but 
only certain files, how do I do that now? thanks

---

### Post by ontherooftop on 2010-02-09
here is what I got 

ubuntu@ubuntu:~$ sudo mkdir /mnt/usbstick
ubuntu@ubuntu:~$ sudo mkdir /mnt/harddrive
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/usbstick
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/harddrive
ubuntu@ubuntu:~$ ls /mnt/harddrive
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old


home is where everything should be.

---

### Post by Joe Ker1086 on 2010-02-09
ok, did you say the total size of this partition that is used is 12gb? if so a good chunk of that is the system files for linux...but im not sure what the total size of your home folder is. try running

```
du -hs /mnt/harddrive/home
```

that will tell us the total size and if we need to split it up or select specific files.

---

