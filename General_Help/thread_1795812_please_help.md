---
title: "please help"
date: 2011-07-03
forum: General Help
---

### Post by ferersoy on 2011-07-03
Hello, Dear Friends
 
I have Dell Latitude 5500 laptop belong to firm. Linux(ubuntu 10.10 ) +windows XP were working together on my laptop .
 
I was copying somethings to CF card via card writer. I wrongly wrote sda instead of sdb and now. I have message on screen, error partition grub rescue > 
 
 
I can't open my laptop now.
 
 
When I put Ubuntu live cd to laptop and I see my HDD under computer and 3 partition 115 MB- 160 GB and 50 GB and when I click on part&#305;t&#305;on I can see inside of the disk.
 
I understud now there is no windows on volume 160GB in HDD but other parts of HDD shows linux files.
 
now my question is ? 
 
can I recover all windows XP files into partition 160GB .
it was including SAP(erp software, outlook and many important documents) 
 
and of course I have to recover Ubuntu 10.10 and OP Selection software ( Ithink you call it Grub) 
 
(there are many recover program but, they work under windows I can't open windows XP , I have just Live CD of Ubuntu and I can start some Linux application ,
I could not see freeware recover program from Linux Terminal for all type disk formats ( I had linux and XP in my HDD)
 
 
 
regards

---

### Post by mikejonesey on 2011-07-03
as u havn messed up the partition table, after installing the grub back over the mba you should be fine, just do a grub-install /dev/sda n update-grub2... once mba is back all should be back to normal...

---

### Post by ferersoy on 2011-07-03
Brother first many thanks , 
 
I m so new for linux but I could not see windowsXP files in the partititon of HDD (160GB) yesterday.
 
 
could you explain me basicly,
 
How can I know ? which one of sda need to write in Terminal of Ubuntu ? 
 
*[COLOR=black](grub-install /dev/sda [COLOR=red]n[/COLOR])[/COLOR]*

I have 3 parts in my HDD 
 
I am able to see from LiveCD
 
 
115 MB -160GB and 49 GB I know that 160 GB for XP and 49GB for Ubuntu
 
I could see partititon on Ubuntu desktop (sudo ls -l) sda1 ,sda2 and sda 3 
 
which sda I need ? 1 or 2 or 3 
 
do I need to write this line on Terminal of the Ubuntu ?(update-grub2)

---

### Post by createdcreature on 2011-07-03
Use cfdisk to wipe your drive and start over. Also, don't title your threads 'help' or 'im in trouble' or whatever, because we don't know what they are.

---

### Post by mikejonesey on 2011-07-03
lol don't wipe your disk lol...

to install grub on mba /dev/sda (no num)

if you wanted to say... install another windows or somthing and then restore grub you would install grub to /dev/sda? ? being your linux partition with linux /boot dir...

in your case just /dev/sda

---

### Post by ferersoy on 2011-07-03
okay I dont wipe   my  disk  
 
thanks I will  write  just   *(grub-install /dev/sda)*
okay  no need to write   number

---

### Post by mikejonesey on 2011-07-03
once you have done this from the livecd boot into the linux partition without the live cd and run;

grub-install /dev/sda
update-grub2

which will ensure you have installed grub from the latest source (with any software updates) there is also a utility that is called comthing along the lines of os-probe which can be useful if windows does not show up in the grub config, you can then run the update-grub2 again after but iv'enever had to use that (grub has always been smart enough to find the correct boot stuff)...

---

### Post by ferersoy on 2011-07-03
> **mikejonesey said:**
> once you have done this from the livecd boot into the linux partition without the live cd and run;

grub-install /dev/sda
update-grub2

which will ensure you have installed grub from the latest source (with any software updates) there is also a utility that is called comthing along the lines of os-probe which can be useful if windows does not show up in the grub config, you can then run the update-grub2 again after but iv'enever had to use that (grub has always been smart enough to find the correct boot stuff)...


if I write   grub-install /dev/sda  

 I  receive  message '' cp: cannot create regular file'
/boot/grub/915resolution.mod':permission  denied


What is your  comment?  thanks

---

### Post by mikejonesey on 2011-07-03
sudo grub-install /dev/sda

---

### Post by ferersoy on 2011-07-03
after  command  promt of  ubuntu
(ubuntu@ubuntu:~$) 

I wrote  this   [COLOR=RoyalBlue]sudo grub-install /dev/sda[/COLOR]

and  answer from Ubuntu  ,

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

when I wrote  this  [COLOR=SeaGreen]sudo grub-install /dev /sda[/COLOR]

and below  answer from Ubuntu


[COLOR=Orange][I]More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit[/I] [I]
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.[/I] [I]

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and[/I] [I]
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy[/I] [I]
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.[/I] [/COLOR]

in this  Case  Which   is  solution   for me ?

Thanks  for your help

---

### Post by mikejonesey on 2011-07-03
hmm i will be goin home shorty to my unix machines (round a friends on a smelly windows machine at the mo...), can give better advice then, in mean time... (from top of my head) you will need to specify the grub root dir for the insall mount the linux drive (can be done be clicking the icon in the places menu), then your grub install cmd should look like;

```
sudo grub-install --root-directory=/media/my-linux-drive-with-boot-dir/ /dev/sda
```

---

### Post by ferersoy on 2011-07-03
Dear Mike,

I have got  hard disk  structure of my computer  maybe  useful for your   advices


ubuntu@ubuntu:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9f1877

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15       24247   194644553    7  HPFS/NTFS
/dev/sda3           24247       30402    49440769    5  Extended
ubuntu@ubuntu:~$ 

[B]I have aimed to recover  WinXP  including (SAP,outlook   and everyting inside of the XP)
[/B]
what will I do  now  ?   I can try  your code: 

thanks

---

### Post by mikejonesey on 2011-07-03
hmm why do i not see a linux partition?

/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15       24247   194644553    7  HPFS/NTFS
/dev/sda3           24247       30402    49440769    5  Extended

unless the extended partiton is labeled incorrectly, (linux partitions reside in logical or primary partitions...)

do a 

ls /dev/

also when you goto menu->places what apears in the menu...

---

### Post by ferersoy on 2011-07-03
Dear mike  ,

below

ubuntu@ubuntu:~$ ls /dev
agpgart          loop3               ram6        tty13  tty41  ttyS3
autofs           loop4               ram7         tty14  tty42  uinput
block            loop5               ram8         tty15  tty43  urandom
bsg              loop6               ram9          tty16  tty44  usbmon0
btrfs-control    loop7               random    tty17  tty45  usbmon1
bus              mapper              rfkill         tty18  tty46  usbmon2
cdrom            mcelog              rtc           tty19  tty47  usbmon3
cdrw             mem                 rtc0           tty2   tty48  usbmon4
char             net                 scd0             tty20  tty49  usbmon5
console          network_latency     sda       tty21  tty5   usbmon6
core             network_throughput  sda1      tty22  tty50  usbmon7
cpu              null                sda2                 tty23  tty51  usbmon8
cpu_dma_latency  oldmem              sda3      tty24  tty52  vcs
disk             pktcdvd             sdb          tty25  tty53  vcs1
dri              port                sdb1               tty26     tty54  vcs2
dvd              ppp                 sg0             tty27     tty55  vcs3
dvdrw            psaux               sg1           tty28    tty56  vcs4
ecryptfs         ptmx                sg2            tty29     tty57  vcs5
fb0              pts                 shm               tty3   tty58  vcs6
fd               ram0                snapshot  tty30  tty59  vcs7
full             ram1                snd       tty31  tty6   vcsa
fuse             ram10               sr0       tty32  tty60  vcsa1
fw0              ram11               stderr    tty33  tty61  vcsa2
hidraw0          ram12               stdin     tty34  tty62  vcsa3
hpet             ram13               stdout    tty35  tty63  vcsa4
input            ram14               tty       tty36  tty7   vcsa5
kmsg             ram15               tty0      tty37  tty8   vcsa6
log              ram2                tty1      tty38  tty9   vcsa7
loop0            ram3                tty10     tty39  ttyS0  vga_arbiter
loop1            ram4                tty11     tty4   ttyS1  zero
loop2            ram5                tty12     tty40  ttyS2

---

### Post by ferersoy on 2011-07-03
mike pardon  this screenshot  better

---

### Post by ferersoy on 2011-07-03
[ATTACH]196608[/ATTACH]

[ATTACH]196609[/ATTACH]

[ATTACH]196610[/ATTACH]

[ATTACH]196611[/ATTACH]

[ATTACH]196612[/ATTACH]

dear mike  ,

please  find  attached   screenshot  from my pc

---

### Post by mikejonesey on 2011-07-03
right i'm back at home...

first thing 1st lets try and install the grub what do you get when you...

1. select Ctrl+l on your 115gb partition this looks like a full linux setup...

from that you can see the location in /media that that drive is mounted...

2. run ```
sudo grub-install --root-directory=/media/???/ /dev/sda
```

??? being the 115 gb dir name

3. paste back ```
mount
``` out of interest...

---

