---
title: "Have i killed my USB Flash Drive?"
date: 2009-07-04
forum: General Help
---

### Post by pokerbirch on 2009-07-04
I have a 4GB Flash drive that i use for general storage/etc which i decided to use for experimental booting of other OS's, including Backtrack. I backed up all my data and formatted the drive into 2 parts using gParted. I did the first partition as EXT2 and 1024MB in size. The remainder of the drive was formatted as FAT32.

I'm not sure what has happened to my drive but it has now become "write protected" and i can't do anything with it. There isn't a read/write protection switch on it and gParted won't let me delete the partitions and start again. FDISK also tells me that the drive is write protected. I'm pretty annoyed with myself. I wish i'd just left it alone.
:(

Will i be able to reformat this drive and/or remove the write protection?

---

### Post by FrogPrince on 2009-07-04
Hi

If I were you, I'd ditch the idea of installing on a USB *stick*. It's possible, a lot of people have done it, but there are dangers. A much better solution is to use an external hard drive. They aren't expensive at all and you'll get much better performance. One of the problems with sticks is that they can be destroyed if you put an OS on them as they can't support the associated stresses and strains  (swapping is out of the question). An external hard drive, however, can cope. I have successfully installed Fedora on an external hard drive which I can plug into a Windows machine and boot. This works so well that, although the performance is very poor compared to a "proper" install, my collegues have been impressed with its performance (I can even get full 3D graphics and the lovely Fedora boot screens). 

Good luck.

---

### Post by pokerbirch on 2009-07-04
Thanks for the reply. My current priority is to get the USB stick working again so that i can continue to use it as a normal storage device. At present it is blank and i can't format it OR write any files to it. I also tried the dd method but that also fails due to the "write protection" problem. I don't understand how or why my flash drive became read-only??

Regarding the testing of other OS's, i was thinking that VirtualBox would be a better solution?

---

### Post by vishal_mala on 2009-07-04
A fried usb drive will never get detected on ur pc, so your drive is all fine, the problem lies somewhere in the drive's partition table, I have mentioned a solution try it, this thing worked on my friend's 2gb Kingston-

Plug in your usb drive, then reboot your computer using the windows xp boot cd. On reaching the partition menu, the place where it shows you your all hard drives and storage media, there you will see he name of your own pendrive, select it and format it in either ntfs or fat, it's ur wish. Just make sure that you do FULL format and not the Quick one.

---

### Post by pokerbirch on 2009-07-04
Hmmmm....tried the XP CD and it found my drive ok but Windows doesn't recognise the 1GB EXT2 partition. It knows it's there, but can't do anything with it. Tried to delete the fat32 partition and then both partitions but Windows says it can't do it. Tried to create new partitions, but again it's a no go. The quick/full format was never an option. I'm stumped, i'm really, really stumped.

Have a copy of the Ultimate Boot CD, so am going to see if any of the tools on there can help me...

---

### Post by iponeverything on 2009-07-04
use gparted to delete all partitions on the flash drive then format it with.

```
mkfs.msdos /dev/<flash disk>

```
where  <flash disk> is your flash disk.

After that you should be good to go.

---

### Post by tgalati4 on 2009-07-04
Windows does not acknowlege the existance of linux.  So the fact that Windows can't see your ext2 partition is not a surprise.  

I have had luck reformatting under DOS using the format command with the proper head, cylinder, sector count.  You can get that count from another identical card that has yet to be overwritten.  You may be able to google the specifications for your card.

Linux tries to format it with head, cylinder, sector counts that work for most hard disks, but the controllers in flash disks need the proper counts to work properly.

---

### Post by t0p on 2009-07-04
You may have to accept the stick is broken.  This happened to me: the stick became read-only, but I could still reformat it in gparted.  So I reformatted it repeatedly, trying out all the filesystem formats I could think of.  That finished it off -reformatting became impossible.

I took the stick back to the store I bought it from, and the manager told me he'd seen this before.  The stick was faulty.  So he gave me a new one. 

> **FrogPrince said:**
> Hi

If I were you, I'd ditch the idea of installing on a USB *stick*. It's possible, a lot of people have done it, but there are dangers...
One of the problems with sticks is that they can be destroyed if you put an OS on them as they can't support the associated stresses and strains  (swapping is out of the question) 


I don't see any problem as long as you save files to another stick or card.  I've had live session Backtrack3, Ubuntu and eeebuntu on sticks with no difficulties.

---

### Post by FrogPrince on 2009-07-04
> I don't see any problem as long as you save files to another stick or card.

As I said, it can be done but I don't think it's advisable. In the long run, repeated writing to USB sticks can damage them: they're not as robust as we like to believe - especially the cheap ones. I myself have damaged a couple by being too "brutal" with them - and incidentally the symptoms were similar as the stick in question here: no write ability and all formatting is fruitless. I agree with you, though, tOp: it looks like a duff and should be taken back.
[Here]("http://www.pendrivelinux.com/recommended-usb-flash-drives/#more-214") is an interesting page on the subject on a very, very good site about Linux on a stick. You'll find just about all your questions answered there.

---

### Post by pokerbirch on 2009-07-04
> **iponeverything said:**
> use gparted to delete all partitions on the flash drive then format it with.

```
mkfs.msdos /dev/<flash disk>

```
where  <flash disk> is your flash disk.

After that you should be good to go.

As stated in my first post, gParted won't allow me to delete the partitions. I get the following error on the "good" FAT32 partition:
```
GParted 0.3.8

Libparted 1.8.9

Delete /dev/sdd2 (fat32, 2.84 GiB) from /dev/sdd  00:00:03    ( ERROR )
     	
calibrate /dev/sdd2  00:00:00    ( SUCCESS )
     	
path: /dev/sdd2
start: 2088450
end: 8048564
size: 5960115 (2.84 GiB)
delete partition  00:00:03    ( ERROR )
libparted messages    ( INFO )
     	
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.
Can't write to /dev/sdd, because it is opened read-only.
Unable to open /dev/sdd read-write (Read-only file system). /dev/sdd has been opened read-only.

========================================
```
...and this...
```
birchy@AMD-Ubuntu:~$ dmesg | tail
[   63.341082] FAT: Filesystem panic (dev sdd2)
[   63.341084]     invalid access to FAT (entry 0x2e3333a3)
[   63.341210] FAT: Filesystem panic (dev sdd2)
[   63.341213]     invalid access to FAT (entry 0x2e3333a3)
[  142.980397] ppdev0: registered pardevice
[  143.028263] ppdev0: unregistered pardevice
[  143.180085] ppdev0: registered pardevice
[  143.228017] ppdev0: unregistered pardevice
[  144.290938] ppdev0: registered pardevice
[  144.340228] ppdev0: unregistered pardevice
birchy@AMD-Ubuntu:~$ GParted 0.3.8

```

---

### Post by pokerbirch on 2009-07-04
Also...just for the record...i've had this stick for around 2 years and have used it purely as a device for "essential" backups of files and programming projects/libraries that i've spent a lot of time developing. It's not really been used a great deal and has been very reliable...so it's definitely not a duffer. It all went wrong after i formatted it with gParted. Luckily i had the sense to backup the data before i wiped it...

Not sure if it's of any importance, but it is a 4GB stick from Play.com with a Phison PS2231 chipset. There should be some sort of "factory reset" feature on this chip. I'll have to look for a datasheet when i have time. Have to go to bed now, in readiness for a 6am start due to a fishing match... 


Further info:
I ran several HDD tools from the UBCD and only HDAT2 supports USB drives. That also says the drive is read-only. It seems that i have nuked it, however every program i've tried recognises it as a 4GB drive, so surely it's not completely lost?

---

### Post by FrogPrince on 2009-07-05
No, not comletely lost. The stick will be recognized if the partition table hasn't been touched, but you may well have a bad sector on it.

---

### Post by iponeverything on 2009-07-05
Can you dd over whole thing and then try to format it msdos

```

sudo dd if=/dev/zero of=/dev/<flash drive>
sudo mkfs.msdos /dev/<flash drive>

```

---

### Post by pokerbirch on 2009-07-05
```
birchy@AMD-Ubuntu:~$ sudo su

root@AMD-Ubuntu:/home/birchy# fdisk -l

Disk /dev/sdd: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfddf42d

Device Boot         Start         End      Blocks   Id  System
/dev/sdd1               1         130     1044193+  83  Linux
/dev/sdd2             131         501     2980057+   b  W95 FAT32

root@AMD-Ubuntu:/home/birchy# dd if=/dev/zero of=/dev/sdd
dd: opening `/dev/sdd': Read-only file system

root@AMD-Ubuntu:/home/birchy# mkfs.msdos /dev/sdd
mkfs.msdos 2.11 (12 Mar 2005)
mkfs.msdos: unable to open /dev/sdd

root@AMD-Ubuntu:/home/birchy# 

```

---

### Post by ju2wheels on 2009-07-05
Ok, as was already stated, if your drive and partitions show up in Linux, its not fried. Secondly, you cant format or change partitions on a drive using Gparted if the partition is mounted. If you opened gparted from the command line, make sure you use sudo.

```
sudo gparted
```

Once you open Gparted, select the correct device that represents your usb drive. Right click on one of the partitions, and if you see the option to "Unmount" available, then select that for each partition on the usb drive. Then go ahead and try to delete the partitions.

FYI, the reason your drive is read-only is because your partition is ext2 and the permissions by default do not allow you writing permission until you chown/chmod them to the correct settings. This read-only issue should not happen for your FAT32/NTFS partitions.

---

### Post by scrooge_74 on 2009-07-05
Have you tried to:

sudo fdisk /dev/(what ever your system says)

then

sudo mkfs -t vfat /dev/(what ever your systems says)

---

### Post by pokerbirch on 2009-07-05
As i stated in posts #1 and #10, gParted isn't able to write any changes to the flash drive. I even tried the Live CD version but no joy. I get the error message:
> Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd has been opened read-only

I've written it off and ordered 2 replacements, however i *would* like to know how the drive became read-only after formatting it with gParted so that i can avoid it in the future...


EDIT:
Ok, it seems that a lot of people are not reading the earlier posts. Just to summarize what i have tried so far:

1. sudo gParted (AND from Live CD) (no go - tells me drive is write protected)
2. all of the HDD tools on The Ultimate Boot CD. Only HDAT2 supports USB drives and wasn't able to write to the drive. States the drive is write protected.
3.```
birchy@AMD-Ubuntu:~$ sudo fdisk /dev/sdd
You will not be able to write the partition table.

Command (m for help): sudo mkfs -t vfat
Building a new Sun disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
contents won't be recoverable.
Command (m for help): w
Unable to write /dev/sdd
birchy@AMD-Ubuntu:~$ 
```
4.```
birchy@AMD-Ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdd
dd: opening `/dev/sdd': Read-only file system
birchy@AMD-Ubuntu:~$ 
```
5. format using Windows XP CD. Drive found ok but Windows is not able to format it. (write protected...i would guess...)
6, delete partitions using the Disk Management Tool from Windows admin tools...another fail...message = "the requested operation cannot be completed because the media is write-protected"

---

### Post by moster on 2009-07-05
Buddy, I hate to recommend something non linux but I see no alternative. My friend had such problem in windows with mp3 player. There is some special tool called HP USB Disk Storage Format Tool. Catch is it is for windows and I hope you have dual boot or win in virtualbox for this one.

[http://files.extremeoverclocking.com/file.php?f=197]("http://files.extremeoverclocking.com/file.php?f=197")

---

### Post by pokerbirch on 2009-07-05
> **moster said:**
> Buddy, I hate to recommend something non linux but I see no alternative. My friend had such problem in windows with mp3 player. There is some special tool called HP USB Disk Storage Format Tool. Catch is it is for windows and I hope you have dual boot or win in virtualbox for this one.

[http://files.extremeoverclocking.com/file.php?f=197]("http://files.extremeoverclocking.com/file.php?f=197")

Tried that one yesterday and surprise, surprise, it says: "The disk is write-protected". I think she be proper shagged.

---

### Post by moster on 2009-07-05
Well, while you are in windows if you do not try it yet try it now. It is one in million but you can try. It is working only in Vista and windows 7.

Open terminal and here is steps, enter it line by line

"diskpart"
"list disk"
"select disk 1" If it is disk 1
"clean"
"create partition primary"
"select partition 1"
"active"
"format fs=fat32"
"assign"
"exit"

---

### Post by sdowney717 on 2009-07-05
[http://m3rlinez.blogspot.com/2007/01/just-rescued-my-write-protected-usb.html](http://m3rlinez.blogspot.com/2007/01/just-rescued-my-write-protected-usb.html)

low level format needed??

[http://bytes2000.wordpress.com/2006/12/03/how-to-fix-an-unreadeable-usb-flash-drive-illustrated/](http://bytes2000.wordpress.com/2006/12/03/how-to-fix-an-unreadeable-usb-flash-drive-illustrated/)

---

### Post by moster on 2009-07-05
I do not know if you are familiar with low level format. I never used on USB sticks but this tool claim it can. If low level format cannot help you then you probably go over 1 mil read/write operation and it is good only for garbage.

[http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/]("http://hddguru.com/content/en/software/2006.04.12-HDD-Low-Level-Format-Tool/")

edit:
ups, guy above was faster..

---

### Post by sdowney717 on 2009-07-05
good confirmation:p
Nothing to loose except some time.

---

### Post by pokerbirch on 2009-07-06
Thanks for your suggestions.

LATEST:
1. tried the Low Level Format tool for Windows as recommended above. It finds the drive ok and recognises that it is 4GB. When i tried to format it, loops through a load of "error at offset..." messages and then finally says "format complete". I had a little moment of happiness but then i discovered that the drive was still exactly the same.

2. can't try the Vista commands as i don't have Vista (Vista was actually the reason why i decided to try Ubuntu...), but i know someone who does. Will see him at work tomorrow.

3. just for the record, i have written the drive off as scrap, BUT i'm now using it as a learning experience. Would be very useful to all of us find out how to remove the write-protection...

---

