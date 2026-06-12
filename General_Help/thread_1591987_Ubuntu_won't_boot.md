---
title: "Ubuntu won't boot"
date: 2010-10-10
forum: General Help
---

### Post by olivaw_daneel on 2010-10-10
I've installed Ubuntu using wubi and around 10 days ago I updated Ubuntu using update manager.

When I restarted my computer and selected to boot Ubuntu it wouldn't boot. Whenever I selected Ubuntu my computer would just restart.

I found a solution to this here: [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30) 

This has been fine the last 10 days and I've done a couple of updates since then with no problems.

However, when I tried to boot Ubuntu this morning it just kept on restarting my computer.

In the same thread I linked to above I saw this post: [http://ubuntuforums.org/showpost.php?p=9647548&postcount=32](http://ubuntuforums.org/showpost.php?p=9647548&postcount=32) and thought I should try this to see if that might fix my booting problem.

Unfortunately this hasn't worked and now whenever I try to boot Ubuntu I'm stuck at the grub prompt and don't know what to do.

Any help would be much appreciated. I'm using a Dell Inspiron 530 with 2Ghz Intel Core2 Duo processor and an Nvidia 256MB Geforce 8600 GT.

---

### Post by Manifest on 2010-10-10
Can you boot up window$?

---

### Post by Rubi1200 on 2010-10-10
You may have to reinstall the Windows bootloader to solve this issue:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by olivaw_daneel on 2010-10-10
> **Manifest said:**
> Can you boot up window$?

Yes I can.

I will give rubi1200's suggestion a try.

---

### Post by olivaw_daneel on 2010-10-10
Oh dear I've got big problems now!

I followed the guide linked to by rubi1200 but now when I restart my computer all I get is an 'error: unknown filesystem' and then the grub rescue prompt. I cannot boot either Windows or Ubuntu.

Here's what I did to get to this point:

1. Typed 

```
sudo fdisk -l
```and got the following output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       38914   302027776    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```2. Then I did:

```
sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo grub-install --root-directory=/media/sda3 /dev/sda
```

3. Then I got the message saying 'installation complete' and restarted my computer

4. However, on load up all I got was 'error: file not found' and the grub rescue prompt

5. I looked through the thread linked to by rubi1200 and found this post: [http://ubuntuforums.org/showpost.php?p=8393469&postcount=52](http://ubuntuforums.org/showpost.php?p=8393469&postcount=52)

6. So I did the following:

```
sudo apt-get install mbr
```then

```
sudo install-mbr /dev/sda3
```

7. Restarted my computer and now I'm getting  'error: unknown filesystem' and then the grub rescue prompt

I've got a bad feeling I've done something very wrong here! Can anyone help at all?

---

### Post by olivaw_daneel on 2010-10-10
Bump.

Sorry I'm desperate here.

---

### Post by bcbc on 2010-10-10
Boot a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results - that will tell us what is wrong.

But generally, you will need to install the Windows bootloader (not grub) if you installed ubuntu using wubi. I suspect that you installed the grub bootloader accidentally, which is why you have a grub rescue prompt.

You can use lilo to reinstall a windows equivalent bootloader (from a live CD)
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
(Ignore all warnings as they don't apply to booting windows)

If you don't have a live CD, use a windows repair disk - for XP  run "fixmbr" and for vista/7 run "bootrec.exe /fixmbr"

Your original problem is probably due to a grub-pc upgrade problem with wubi. But get windows booting first and then you can deal with that.

And ps, none of what you've done should have damaged anything - the bootloaders look bad when they don't work but don't generally affect the OS and data (ignoring for a moment the 10.04 bootsector issue that should be solved now)

---

### Post by olivaw_daneel on 2010-10-10
Thanks for your response bcbc. I've posted my results from the bashinfoscript below.

Should I go ahead with your lilo suggestion?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   625,139,711   604,055,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-0A1F                              vfat       DellUtility                   
/dev/sda2        8CF899C5F899ADC8                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 20 63  |.............. c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by bcbc on 2010-10-10
no... you seem to have a serious problem. /dev/sda3 is supposed to be your windows but bootinfoscript cannot see anything on it.

Grub in the bootloader is pointing to /dev/sda3 and I can only imagine that it has damaged the partition bootsector. I don't know what to suggest, but installing the windows bootloader is unlikely to work.

I would recommend using a windows repair disk perhaps. Or maybe testdisk can recover and repair the bootsector - see this link [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)  
But this looks different to the symptoms when just the bootsector is overwritten.

---

### Post by olivaw_daneel on 2010-10-10
I followed the instructions on the testdisk site and when I rebooted rather than getting 'error: filesystem unknown' now I'm getting 'error: file not found'.

I did the bashinfoscript again and you'll notice below that there does seem to be something at dev/sda3 now.

Any more thoughts?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   625,139,711   604,055,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       149ac212-f84f-4721-9022-5b565edbf05d   ext4                                     
/dev/sda1        07D7-0A1F                              vfat       DellUtility                   
/dev/sda2        8CF899C5F899ADC8                       ntfs       RECOVERY                      
/dev/sda3        72829D44829D0DAB                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by bcbc on 2010-10-10
Ok great, now install the bootloader. Either lilo as I showed above or windows bootloader from a windows repair disk.

---

### Post by olivaw_daneel on 2010-10-10
bcbc you are an absolute life-saver.

I can boot up Windows now yay!

If I try and boot Ubuntu, however, I get taken to the grub prompt screen. You said in an earlier post I can't boot Ubuntu "due to a grub-pc upgrade problem with wubi."

Any ideas on how that could be fixed?

Thanks so much for your help.

---

### Post by bcbc on 2010-10-10
> **olivaw_daneel said:**
> bcbc you are an absolute life-saver.

I can boot up Windows now yay!

If I try and boot Ubuntu, however, I get taken to the grub prompt screen. You said in an earlier post I can't boot Ubuntu "due to a grub-pc upgrade problem with wubi."

Any ideas on how that could be fixed?

Thanks so much for your help.

you're welcome... glad it worked out. 

try
```
configfile (hd0,3)/ubuntu/winboot/wubildr.cfg
```

---

### Post by bcbc on 2010-10-10
never mind... you seemed to have gotten rid of /boot/grub/grub.cfg (if you followed instructions in that second link of your first post). 

try this instead.
```
insmod ntfs
set root=(hd0,3)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

After booting, run 
```
sudo update-grub
sudo cp /host/wubildr /host/wubildr.backup
sudo grub-install /dev/sda3

```
The last command will update the wubildr file that's required to boot wubi ubuntu. If it complains do not supply the --force parameter.

If you actually upgraded to 10.10 then this probably won't help. If this is the case, or the instructions above didn't work, then loopmount the root.disk and edit the grub.cfg deleting everything above the first "menuentry". Note you'll have to reapply this workaround whenever you update a kernel and certain other updates.

You might want to consider migrating wubi to a partition install if you  intend to use it in the future. Wubi's pretty unstable at the moment thanks to grub-pc wreaking havoc with it. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by olivaw_daneel on 2010-10-10
Unfortunately none of the things you've mentioned are working for me.

I tried doing the 'insmod ntfs' stuff at the grub prompt but after 'boot' my computer restarted and when I tried to start ubuntu i just got taken to the grub prompt.

I thought maybe I had to boot from the live CD again so I did that but when I enter 

```
sudo update-grub
```

I get the following error:

```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

I tried loopmounting the root.disk (I assumed that was the same thing as what I did here: [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30)) but when I edit the grub.cfg there's nothing in there. Like you said in your post I had deleted the grub.cfg earlier so (unless I'm missing something) I don't know why there would be anything there.

Dunno if I've done anything wrong with the directions you've given me.

---

### Post by bcbc on 2010-10-11
The only other things I could suggest are fsck'ing the root.disk as per the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?"). But if you can already loop mount it I don't know if that would do anything. At the least, backup your data the next time it's mounted.

I think it's strange that entering the manual commands and then 'boot' would cause a restart. I'd expect some sort of message before you entered boot. That's puzzling. But it's hard to know what's happened up until now.

I don't really have any other ideas.

PS running update-grub from a live CD does nothing. You have to boot or chroot into your install first.

---

### Post by olivaw_daneel on 2010-10-11
Seems like the easiest thing to do would be migrate wubi to a partition install although I guess I've got to be able to boot into Ubuntu to do that.

I'll try the fsck thing tonight.

One question about having the Ubuntu partition: am I still able to access files from Windows if I do this?

With wubi I can go into the 'host' folder and access files from there and open them in Ubuntu. Is this something I can still do with a partition?

Thanks again.

---

### Post by bcbc on 2010-10-11
Yes you can access files from the windows partition. Except it won't be /host anymore - it will show up under the Places menu as a separate entry (with a disk drive icon next to it). You will have to mount it first, either manually by clicking it under Places, or automatically by creating an entry in /etc/fstab.

If that fsck doesn't work then you could always run a chkdsk from windows as well. (From My Computer, right-click on the c: drive, Properties, Tools, Check for errors, Automatically fix - usually requires a reboot).

---

### Post by olivaw_daneel on 2010-10-12
I've tried both the fsck and chkdsk but I'm still being taken to the grub prompt screen when I try to boot Ubuntu.

Is it possible for me to create a new grub.cfg (if the contents are available somewhere on the net) and then delete everything above the first 'menuentry' like you said in a previous post?

---

### Post by bcbc on 2010-10-12
> **olivaw_daneel said:**
> I've tried both the fsck and chkdsk but I'm still being taken to the grub prompt screen when I try to boot Ubuntu.

Is it possible for me to create a new grub.cfg (if the contents are available somewhere on the net) and then delete everything above the first 'menuentry' like you said in a previous post?

Try entering the following and tell me what you see:
```
insmod ntfs
set root=(hd0,3)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
ls -l /boot
```

(Those are lower case L's, not 1's) Also describe in detail (version number) what the grub screen looks like.

---

### Post by olivaw_daneel on 2010-10-12
Ok so the GNU grub version is 1.98-1ubuntu-7

When I enter those commands I get like a 3 column, 15 row table. The top row is:

```
DIR     20101010092121      grub/
```

There is then a list of DIR numbers under 'DIR' in the left-hand column and the middle column always has numbers beginning with '2010'.

The right-hand column has things like:

```
system.map-2.6.32-21-generic
```

and

```
vmlinuz-2.6.32-25-generic
```

I can write out the full table if you need it (although I'm hoping not :) )

Thanks.

---

### Post by bcbc on 2010-10-12
> **olivaw_daneel said:**
> Ok so the GNU grub version is 1.98-1ubuntu-7

When I enter those commands I get like a 3 column, 15 row table. The top row is:

```
DIR     20101010092121      grub/
```

There is then a list of DIR numbers under 'DIR' in the left-hand column and the middle column always has numbers beginning with '2010'.

The right-hand column has things like:

```
system.map-2.6.32-21-generic
```

and

```
vmlinuz-2.6.32-25-generic
```

I can write out the full table if you need it (although I'm hoping not :) )

Thanks.

OK that's good - it's mounting the root.disk properly. Now add in the following lines and if it still reboots, try changing the kernel numbers i.e. if -25 doesn't work, try -24:
```
linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.32-25-generic
boot
```

---

### Post by olivaw_daneel on 2010-10-13
I've tried -25, -24 and -21 but my computer just restarts every time. No error message or anything.

---

### Post by bcbc on 2010-10-13
Try "ro single" instead of "ro quiet splash" to boot to recovery mode.
You might as well try "ro noacpi noapic" while you're at it.

I'm running out of ideas. The only other thing would be to chroot and try and reinstall the kernel, but that seems like a lot of work without any real idea whether it will fix the problem.

I'd start thinking about recovering your data and, after that, reinstalling.

---

### Post by corcomp84 on 2010-10-13
Well first of all how much data do you have on ubuntu?  if not to much then boot into with a live CD and save it to a flash drive.. ok second problem when you upgrade using the manager you have a very good chance of everything messing up.. thats why its best to keep your files organized and a list of your programs available so that you can simply do a clean install.. I would stop wasting your time with trying to repair it and just do a clean install with the live CD.. That way it will install a new grub loader because the MBR sucks and a whole new kernel.. then if you don't play around with Ubuntu for the fun of it then I would just install 10.04 because its a long term release and will keep you happy for well into two years.. It only takes about an hour and a half to install Ubuntu so long as you already downloaded the ISO.. but this is just my opinion..

---

### Post by olivaw_daneel on 2010-10-13
I've copied the ubuntu folder located on my Windows OS onto a portable hard drive.

Maybe it would be easiest to just do a proper install of Ubuntu.

How would I access the data that I stored on my ubuntu wubi installation? At the moment in my ubuntu folder it's just .disk and wubildr files.

Thanks

---

### Post by corcomp84 on 2010-10-13
what kind of data is it,, pics, music, ?.. And did you try booting into the live CD and accessing the flash drive from there.. maybe it will automatically see it..

---

### Post by bcbc on 2010-10-13
You can either loopmount the virtual disks from a live CD (or a future ubuntu install) - you've done this already to edit grub.cfg. 

Or you can install a tool like Ext2Read 2.2 ([http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)) that can read ext4 partitions and virtual disks. Just point it at each .disk file and then you can copy your data off it.

---

### Post by olivaw_daneel on 2010-10-13
Ah yes I just mounted it on the live CD and was able to access everything.

Anyway I'm going to go ahead with this proper Ubuntu install now so hopefully I won't have to write in this 3 page thread again!

Thanks for your help - especially to you bcbc your responses have not only been extremely helpful but lightning fast too. It's been much appreciated.

---

### Post by bcbc on 2010-10-13
> **olivaw_daneel said:**
> Ah yes I just mounted it on the live CD and was able to access everything.

Anyway I'm going to go ahead with this proper Ubuntu install now so hopefully I won't have to write in this 3 page thread again!

Thanks for your help - especially to you bcbc your responses have not only been extremely helpful but lightning fast too. It's been much appreciated.

You're welcome. :)  Sorry it didn't work out, but you'll be happier with a normal install.

PS backup your windows data too. Partitioning does carry some risks.

---

