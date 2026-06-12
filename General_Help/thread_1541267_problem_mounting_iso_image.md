---
title: "problem mounting iso image"
date: 2010-07-28
forum: General Help
---

### Post by cadogan281 on 2010-07-28
i created an img from an camera photo sd card.the image came out fine,and i changed it from .img to .iso to mount in ubuntu.when i try to mount it,i get an error similar to this:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
 missing codepage or helper program, or other error
 In some cases useful info is found in syslog - try
 dmesg | tail  or so


i have been trying to mount it like this:

sudo su mount -t ext2 -o loop,ro,sb=131072 123.iso /mnt

i found a website that has a fix for it but i couldnt get it too mount right.
the .iso image is on my desktop,but iam not sure how to mount it like they do.
here is the webpage describing how to mount it properly:

[http://blogs.sans.org/computer-forensics/2009/10/05/mounting-images-using-alternate-superblocks-follow-up/](http://blogs.sans.org/computer-forensics/2009/10/05/mounting-images-using-alternate-superblocks-follow-up/)

i need it mounted i guess as either a hard drive or cdrom for when i use the program photorec.the image filesystem is either
fat 16 or fat 32.can anyone please help me on getting it mounted right?thanks

---

### Post by chopinhauer on 2010-07-28
> **cadogan281 said:**
> 
sudo su mount -t ext2 -o loop,ro,sb=131072 123.iso /mnt


If it is a image of your camera SD card, it does not contain an ext2 filesystem, but a fat32 filesystem. So the option to mount it is '-t vfat' or together:
```
sudo mount -t vfat -o loop,umask=000,ro <your filename> /mnt
```

I added 'umask=000' to the options, so every user on your computer can access the files and you don't need to run big graphical programs as root.

---

### Post by cadogan281 on 2010-07-28
i tried it and i got this:

Desktop$ sudo su
root@cadogan-desktop:/home/cadogan/Desktop# sudo mount -t vfat -o loop,umask=000,ro <cf.iso> /mnt

bash: /mnt: Is a directory


without the brackets and i get this:

Desktop# sudo mount -t vfat -o loop,umask=000,ro cf.iso /mnt

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

it looks like the first one is trying to work but it says its a directory.iam on the desktop where the image file is as well.any ideas what else i can try?also the program gmount-iso gave me the same error as above.

---

### Post by iponeverything on 2010-07-28
what command did you use to create the image?

run:

```
file 123.iso
```

also try:

```

mkdir image
mount -o loop 123.iso image

```

---

### Post by cadogan281 on 2010-07-29
i just renamed it .iso. someone on a different board said it was fine to do it that way.ill try those out and let u know how it goes.here is what file cf.iso came up with:

Desktop$ file cf.iso
cf.iso: x86 boot sector, Microsoft Windows XP mbr; partition 1: ID=0x6, active, starthead 1, startsector 32, 125152 sectors, code offset 0x33

i ran this:

mkdir image
mount -o loop cf.iso image

and this was the output:     

mount: you must specify the filesystem type

so it sounds like were getting close to getting it working.

---

### Post by iponeverything on 2010-07-29
Your going to have to mount the image with an offset.

Run:
```

fdisk -ul 123.iso

```
It should print out something like:

```

Disk 123.iso: 0 MB, 0 bytes
32 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes

             Device Boot      Start         End      Blocks   Id  System
           123.iso1   *          63      499967      249952+  83  Linux
           123.iso2          499968      999935      249984   83  Linux

```

Determine the offset by multiplying the partition start sector with block size. So, if in the above example, you wanted mount the first partition:

determine the offset 512*63 = 32256

mount the partition:

```
mount -o loop,offset=32256  123.iso /mnt
```

---

### Post by cadogan281 on 2010-07-29
i was having another problem,but here are the commands leading up to it:

Disk cf.iso: 0 MB, 0 bytes

8 heads, 32 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

 Device Boot      Start         End      Blocks   Id  System
cf.iso1   *          32      125183       62576    6  FAT16

i multiplied the 512x32 and got 16384.so then i did this command,but got an error about the -o option:

sudo su mount -o loop,offset=16384 cf.iso /mnt
su: invalid option -- 'o'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and
                                keep the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

---

### Post by iponeverything on 2010-07-29
```
sudo su mount -o loop,offset=16384 cf.iso /mnt
su: invalid option -- 'o'
Usage: su [options] [LOGIN]
```

you had "sudo su" leave out the "su"

```
sudo mount -o loop,offset=16384 cf.iso /mnt
```

---

### Post by cadogan281 on 2010-07-29
thanks you so much it worked!!! :D i have been trying to figure it out for the longest time.thanks for everyones help.:popcorn:

just one more thing,what is the difference when i did sudo su and just sudo?isnt sudo su for logging into your root account?

---

### Post by iponeverything on 2010-07-30
> **cadogan281 said:**
> thanks you so much it worked!!! :D i have been trying to figure it out for the longest time.thanks for everyones help.:popcorn:

just one more thing,what is the difference when i did sudo su and just sudo?isnt sudo su for logging into your root account?

sudo is running commands as another user and su is to change to another user. 

so by running sudo su the effect is a root shell.

---

