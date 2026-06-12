---
title: "Copying everything"
date: 2011-12-10
forum: General Help
---

### Post by Yinepu on 2011-12-10
I can't seem to boot from a USB or CD on my desktop PC to install anything, yet I can plug my HDD into my PC which it seems to boot off fine and load into Ubuntu. A blank HDD is also in it, and I was wondering if it was possible to copy everything from the laptop HDD to my desktop's HDD including all the system files? I tried it and I don't have sufficient privileges to copy certain files because they are owned by the 'root' account....

---

### Post by haqking on 2011-12-10
> **Yinepu said:**
> I can't seem to boot from a USB or CD on my desktop PC to install anything, yet I can plug my HDD into my PC which it seems to boot off fine and load into Ubuntu. A blank HDD is also in it, and I was wondering if it was possible to copy everything from the laptop HDD to my desktop's HDD including all the system files? I tried it and I don't have sufficient privileges to copy certain files because they are owned by the 'root' account....

you could clone it using [clonezilla]("http://www.clonezilla.org")

however if you ever want to copy things owned by root then use sudo...see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Mark Phelps on 2011-12-10
> **Yinepu said:**
> I can't seem to boot from a USB or CD on my desktop PC to install anything, yet I can plug my HDD into my PC which it seems to boot off fine and load into Ubuntu.

Do you have your desktop set to boot from an external drive automatically?  And thus, did you install or configure GRUB to it only looks on the external drive for boot files?

If these are true, that could be why you can't boot otherwise.

---

### Post by Yinepu on 2011-12-10
No, all the drives are internal. I've connected and I'm running the laptop HDD through a mini to regular PATA converter. I just can't copy the files, that's all, it boots fine. The reason I can't boot from CD or USB is because it's such an old PC the BIOS utility doesn't give that option, I don't know what's with the CD/DVD drive.

---

### Post by haqking on 2011-12-10
like i said you can clone it, or if you want to use a copy command then the privelege issue is solved by using [rootsudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Yinepu on 2011-12-10
Well, I tried those and I don't have any spare CDs to burn the clone tool onto, and I tried the root thing and it said the same thing about not having sufficient privileges....

---

### Post by haqking on 2011-12-10
> **Yinepu said:**
> Well, I tried those and I don't have any spare CDs to burn the clone tool onto, and I tried the root thing and it said the same thing about not having sufficient privileges....

well wait until you can buy a CD then, they are not expensive, or stick it on a USB.

and are you a admin user then so you can use sudo ?

example:

```
sudo <copycommandofchoice>
```

then you enter your own password to perform the sudo action

show us a screen dump, it is apparent you are doing something wrong

---

### Post by Yinepu on 2011-12-10
But it can't boot off CD or USB anyway, it can only boot from specific CDs and USBs for some reason, it will only work with Windows CDs, not UNIX ones I think, and to boot from USB I have to pull out all the HDDs until it thinks that the USB is the HDD which kind of defeats the purpose. I'll try it again anyway.

---

### Post by N00b-un-2 on 2011-12-10
I doubt your computer is incapable of booting from a Linux CD.  If it can boot from a Windows CD, it can boot from Linux CD.  More than likely it has difficulty booting from a CD-R because it has an older CD-ROM drive with a weak laser.  I would say to try burning again at the slowest speed possible and verifying the data when your done but you said you don't have any more CD-Rs.  Is getting more CD-Rs not an option for some reason?  That being said,  many older computers do not have the ability to boot from USB.  Is network booting an option for you?

---

### Post by Yinepu on 2011-12-10
Oh, right that's probably why. I'll try a slower speed. And I can boot off USB, but I can't remember how, and last time I had to remove my HDD. I'll have a fiddle about with the boot order.

---

### Post by Yinepu on 2011-12-10
And by that do you mean type sudo cp -R /media/f044be81-caad-4224-9d5d-a4e50a9dc23e /media/HDD?

---

### Post by haqking on 2011-12-10
> **Yinepu said:**
> And by that do you mean type sudo cp -R /media/f044be81-caad-4224-9d5d-a4e50a9dc23e /media/HDD?

well i dont know what the path is but yes append sudo to any copy action and it should ask for a password, that password is yours if you are in the sudo group and this be able to carry out root tasks

gksudo if graphical

---

### Post by Yinepu on 2011-12-10
"cp: cannot stat `/media/f044be81-caad-4224-9d5d-a4e50a9dc23e': No such file or directory", well that's different but I'm still not getting anywhere.

---

### Post by haqking on 2011-12-10
> **Yinepu said:**
> "cp: cannot stat `/media/f044be81-caad-4224-9d5d-a4e50a9dc23e': No such file or directory", well that's different but I'm still not getting anywhere.

well you havent specified anything to copy.

I presume that f044be81-caad-4224-9d5d-a4e50a9dc23e is the name of your drive you are trying to copy from.

you need to specify what like *.* for all files.

however this is not the best way to this.

i suspect dd or rsync will be much better for want you want ?

do you want an image or copy every single file from one location to another ?

---

### Post by Yinepu on 2011-12-10
Oh, wait, I'm copying from the wrong partition. But it still doesn't work, I'm now trying to copy the new system to it which is in the "/" location, and then I put "sudo cp -R /*.* /media/HDD" it just takes a new prompt line, when I do it without the "*.*" it still shows privilege messages.

---

### Post by winh8r on 2011-12-11
The best way to copy HDD to HDD is , as was suggested already, use the dd command.The syntax will be something like this: 

dd if=/dev/sda2 of=/dev/sdb2 bs=4096 

You will need to change the "sda2" and "sdb2" entries to correspond to what your respective drives are named.

the first entry is the source HDD and the second entry is the destination HDD.

Open a terminal and type in         "man dd"      (without the quotes!")
this will give you a lot more information, you can also just type 
"dd --help" for a shorter version of the help and options.

It is important that the source HDD is of a lower capacity than the destinatio HDD, as this would cause obvious problems if this was not the case.

Hope this is of some help.

---

### Post by Yinepu on 2011-12-12
Well I put dd if=/dev/f044be81-caad-4224-9d5d-a4e50a9dc23e of/dev/HDD bs=4096, is that right? Because I'm getting this error: 
dd: unrecognized operand `of/dev/HDD'
Try `dd --help' for more information.

---

### Post by N00b-un-2 on 2011-12-12
> dd: unrecognized operand `of/dev/HDD'

first of all, dd is used to copy devices locations not file locations.  what you need to do is determine which /dev/sdXX is /media/f044be81-caad-4224-9d5d-a4e50a9dc23e.  Use 
```
sudo fdisk -l
```
If /media/f044be81-caad-4224-9d5d-a4e50a9dc23e is an external hard drive or USB thumb drive its going to be /dev/sdb1 or higher.  /dev/sda is going to be the hard drive inside your computer.

you can either clone the file system on /media/f044be81-caad-4224-9d5d-a4e50a9dc23e to another partition using for example
```
sudo dd if=/dev/sdb1 of=/dev/sda2
```

or you can export the output to an file system location somewhere on your hard drive by providing the absolute path, provided the absolute path exists before executing dd. eg;

```
mkdir /home/user/backup
sudo dd if=/dev/sdb1 of=/home/user/backup
```

Second of all, the reason why its giving you that error is because the command you issued is missing an equal sign but at the rate you're going you stand the risk of nuking your hard drive issuing sudo dd without knowing EXACTLY what you're doing.

seriously.  stop and think before you break your computer.  Post the output of 
```
sudo fdisk -l
```
and we'll go from there.

---

### Post by Yinepu on 2011-12-12
All drives come up as "/dev/sdc[number]", and it's not USB, it's an internal HDD, but I still can't determine which one it is out of the listed ones.

---

### Post by spiky001 on 2011-12-12
Disc uttility will give you the uuid and dev partition mounted at number or ```
blkid
```

---

### Post by N00b-un-2 on 2011-12-12
each partition is going to be /dev/sdcX something.  please post the output of fdisk like I said.  if you know the size of the partition at least I can help you from there.

---

### Post by Yinepu on 2011-12-12
Oh, whoops, never read on. Anyway, output of that is:


Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82688268

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    28700904    14350421   83  Linux
/dev/sda2        28702718    58605119    14951201    5  Extended
/dev/sda5        57239658    58605119      682731   82  Linux swap / Solaris
/dev/sda6        28702720    56258559    13777920   83  Linux
/dev/sda7        56260608    57239551      489472   82  Linux swap / Solaris

Partition table entries are not in disk order
omitting empty partition (5)

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    40387409    20193673+   7  HPFS/NTFS/exFAT
/dev/sdb2        40402942    78163967    18880513    5  Extended
/dev/sdb5        76496896    78163967      833536   82  Linux swap / Solaris

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c19e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     7372799     3685376   83  Linux
/dev/sdc2         7374846     7829503      227329    5  Extended
/dev/sdc3   *      491904     7831151     3669624    c  W95 FAT32 (LBA)
/dev/sdc5         7374848     7829503      227328   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x013c27ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   976768127   488384032+   7  HPFS/NTFS/exFAT

---

### Post by N00b-un-2 on 2011-12-12
WTF over!?  /dev/sda has two swap partitions.  That just doesn't make any sense.  /dev/sdb has swap as well.  Why?  I'm assuming since it's NTFS and marked as boot its your Windows hard drive?  But you have another large NTFS partition on /dev/sdc, also marked as boot and YET ANOTHER swap.  And then /dev/sdd has only one NTFS partition.
Dude, before you proceed you need to explain what is going on with your partitioning.  Unless you're running three separate Linux distros and at least two versions of Windows, I can't make any sense of it.  I can't imagine any reason why you need more than ONE swap space PERIOD.  Much less four on three separate drives.

At this point you need not worry about trying to dd what I'm assuming is a linux install over another linux install, doing so is probably not going to result in a bootable system anyway.  You need to properly back up your files, reformat your hard drive(s) and install a fresh copy of Linux and/or Windows.

---

