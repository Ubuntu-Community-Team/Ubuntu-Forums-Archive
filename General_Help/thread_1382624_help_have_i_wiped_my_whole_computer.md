---
title: "help have i wiped my whole computer???"
date: 2010-01-16
forum: General Help
---

### Post by nervousnath on 2010-01-16
recently install ubuntu 9.10, after a repartition and rebootall that came up was:
 
grub loading
no such partition
grub rescue>

so after looking around i found a guide to restore the boot loader so i entered 
 'sudo fdisk -l into the terminal and came up with the details of my lonely hard disk with no partitions!!!

now gparted on the livecd only comes up with 1 'unallocated' /dev/sda.

please help

nervousnath

---

### Post by nervousnath on 2010-01-16
also.....maybe coz my partition table is gone?

---

### Post by jamesisin on 2010-01-16
That doesn't sound good.

What more can you say about this "repartition" that you did?

---

### Post by nervousnath on 2010-01-16
i had partitioned the reccommended amount of disk space during the install but i wanted some more, so i used gparted on the live cd to shrink down my windows partition some more. once it finished i was fumbling around to work out how to then increase my ubuntu partition with the new available space. then i accidentaly clicked on something, no idea what and all my partition data was gone. from looking around i think i deleted the partition table?

---

### Post by garvinrick4 on 2010-01-16
Unallocated is not a good thing. Install your Windows as NTFS when asked what format type.
XP, uses less primarys than Vista or 7 you did not say which you use. Any way after you install
Windows do the Ubunu install, tell the size when gparted asks and it will give you your partition
table if you let it by NOT choosing Manual. If you like what you see tell it to finish. It will install
ext4 and grub2 by default in 9.10 installation disk and make sure the types of partitions are correct. Remember Windows will only reside in Primary partitions from get go. You can have an extended partition (which is primary) and have all the logical's partitions you like inside of the extended which Linux can reside. gparted is a great piece of software but you must stay focused when using. Only use manual install if you know what you are doing if not read or let it do its thing.  Have a nice day. One thing to remember is you are only allowed 4 primary Partitions and Windows 7 and Vista take three if Boot partition or system ( is sda1 for instance) as /boot and
sda2 is where C: resides or (OS) and then one for recovery. / in Linux is same as C: in Windows. (OS)  Link will give you a nice understanding.

[GParted partitioning software - Full tutorial]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by nervousnath on 2010-01-16
ok ..so im kinda confused.
im using vista (which i really dont like btw)
@garvinrick4 - so your saying if i reinstall ubuntu and vista it'll pretty mcuh work itself out and ill be back to start?

if my computer isnt wiped and all it is it the partition table is gone, how will this help? i had already installed ubuntu and was changing partition sizes when (i think) i deleted the partition table

---

### Post by nervousnath on 2010-01-16
im going to try and use testdisk but i dont know how to to install it

---

### Post by garvinrick4 on 2010-01-16
If you have another computer download gparted iso burn it to disk and you will be able to
look at your disk. I assume it is unallocated to anything. If you have a live ubuntu CD (the install disk) use it. gparted will tell you what you did. Maybe all you have to do is reinstall grub2. You have to look at partition table. Or run "fdisk -l" without qoutes and that is small
L in Live CD in a Terminal. It will tell you what your Table is and where boot is. Post it to this Thread. Lots of ways to see what is doing with a Live CD. If Vista and Ubuntu are new installs just start over. If you got info in there you need lets fix er up. Lots of people here know there way around grub, live cd's, gparted. Do not worry all will work out.

---

### Post by nervousnath on 2010-01-16
ok so i ran testdisk and went through the process, it did find my partitions again and after it finished i had to reboot. 
it still didnt boot up, now  the grub message slightly changed

grub loading
error: unknown filesystem
grub rescue>

i am using my ubuntu 9.10 livecd at the moment with gparted on it, do i need a separate gparted iso?

after running fdisk -l in the terminal it comes up with:
       ubuntu@ubuntu:~$ sudo fdisk -l
   
  Disk /dev/sda: 320.1 GB, 320072933376 bytes
  255 heads, 63 sectors/track, 38913 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0x3f3f49cc
   
     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1   *           1       25740   206748512+   7  HPFS/NTFS
  /dev/sda2           32832       37255    35535748   83  Linux
  /dev/sda3           37256       37450     1566296   82  Linux swap / Solaris
  /dev/sda4           37451       38914    11759580    f  W95 Ext'd (LBA)
  /dev/sda5           37451       38913    11750400    7  HPFS/NTFS
  ubuntu@ubuntu:~$




so im pretty sure it couldnt do that before so i think ive made some progress, however gparted still is unchanged and is as 'unallocated' as ever

---

### Post by nervousnath on 2010-01-16
after more messing around, the gparted is still unallocated but the disk utility shows all the partitions, and they have a 'bootable' option check box, i tried to check the corresponding partition and apply the changed but this is what came up:


   Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=270044199936, new_start=270044199936, new_size=36388605952, type=0x83
  Entering MS-DOS parser (offset=0, size=320072933376)
  MSDOS_MAGIC found
  looking at part 0 (offset 1048576, size 211710476800, type 0x07)
  new part entry
  looking at part 1 (offset 270044199936, size 36388605952, type 0x83)
  new part entry
  looking at part 2 (offset 306432838656, size 1603887104, type 0x82)
  new part entry
  looking at part 3 (offset 308036736000, size 12041809920, type 0x0f)
  Entering MS-DOS extended parser (offset=308036736000, size=12041809920)
  readfrom = 308036736000
  MSDOS_MAGIC found
  Exiting MS-DOS extended parser
  Exiting MS-DOS parser
  MSDOS partition table detected
  containing partition table scheme = 0
  got it
  Error: Can't have a partition outside the disk!
  ped_disk_new() failed

---

### Post by garvinrick4 on 2010-01-16
Partner I would just start the process over and reformat the whole drive NTFS and install
Vista. Then take your Ubuntu CD and install 9.10 tell it the size you want and let it do the
rest. Do not use Manual install. Will not take to long at all, trying to fix that mess make you
want to run around like a crazy man. I would rather see sda1 and sda2 the first two and then
if there is a need for extended be sda3 or sda4 and the other that is not extended sda3 or sda4
the Vista D: drive and the Linux inside the extended partition. If you notice the * that is next
to sda1 that means it is the boot. That was good. sda2 should really be NTFS and the OS for Vista. 
 If you install Vista first gparted will make it so and put Linux in right partition and put your grub2 in the right spot to give you a nice little boot menu and be able to locate the Linux kernel.
In other words it looks a little screwing right now do it over to save yourself problems. And if
later you want to add another Linux it will fit right in.

---

### Post by jamesisin on 2010-01-16
Isn't the OP trying to salvage data?  If not, then you are probably correct.

---

### Post by nervousnath on 2010-01-17
...so basically im screwed?

---

### Post by jamesisin on 2010-01-17
Do you have data on that drive which you are working to salvage?

---

### Post by nervousnath on 2010-01-17
yeah i really want to save it if i can

---

### Post by SPr on 2010-01-17
Have you tried reinstalling Grub from the Ubuntu Live CD? When booting from the CD you should get an option called something like "Rescue a broken system". If you follow that there ought to be an option to reinstall grub.

---

### Post by nervousnath on 2010-01-17
at live cd boot my options are 

try ubuntu etc etc
instal ubuntu
check disk for defects (done and no defects came up)
test memory
boot from first hard disk

how else could i reinstall the grub?

---

### Post by SPr on 2010-01-17
[http://www.google.com/linux?hl=en&q=reinstal+grub&btnG=Search](http://www.google.com/linux?hl=en&q=reinstal+grub&btnG=Search)

Take your pick. 

I'm surprised that the rescue option has been dropped from the Live CD.

---

### Post by jamesisin on 2010-01-17
Well, if you have an external drive you could potentially boot into the live CD, attach the external drive, mount the various partitions, and copy all that important data to the external drive.

---

### Post by nervousnath on 2010-01-19
ok so how do i mount the partitions?
i took  it to the closest pc support shop and they wanted $330 to recover the data and then another $200 to install windows with more software i apparently needed but they couldnt nesessarily list.
 a friend suggested i take out my laptop hd out and use it as an external drive temporarily and transfer my data to another computer or external  hd then put the laptop hd back and then wipe the laptop, with my data copied to the other computer, and transfer it back over once ive setup my new empty laptop. good idea?

---

### Post by jamesisin on 2010-01-19
Pulling the external hdd and using another machine to pull the files is roughly equivalent to what I suggested above.  In each case you are using a working operating system to browse your laptop hdd in order to copy off important, salvageable files.

You can mount drives in Ubuntu using the mount command.  Check the man page to see usage.  You may find some use in this post:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

The discussion of mounting drives is about half way through the article.

---

### Post by nervousnath on 2010-01-22
thanks, a friend suggested that, 
im going to try that and see how it goes.
if not, when i got my laptop back from the shop they left a data recovery software cd in the drive. so if that doesnt work im just going to run that.

ill keep post results when i get them

---

