---
title: "Drive/partition labelling problems part 1"
date: 2012-05-17
forum: General Help
---

### Post by colin.p on 2012-05-17
I have an ageing Dell 1545 that I run 12.04 on exclusively. However, I have been experiencing some drive labelling problems of late. It is partitioned rather strangely, as I have just removed the last vestiges of Dell's partitioning scheme.

I removed the small Dell Utilities partition as well as the Recovery partition, at the begining of the drive, and combined them with the empty space vacated by Win7 (that I removed when I first installed 10.04, two years ago), making sda1 one whole partition at the beginning of the drive. I originally had 10.04 as a dual boot with win 7 and when I removed 7, I left the partitiong as is for 12.04.

Sda5,6 and 7 are root, swap and then home, with sda1 and 2 the two Dell partitions I have now removed and combined with sda3 making a large sda1. The problem I have is with the two ntfs external drives, sdb1 is a 2T WD Elements drive and sdc1 is a generic 500 GB drive that used to be labelled "new volume". When I boot up, I get a grub recovery prompt if sdc is plugged in, without it, I get an error message that it can't be mounted and I press "s" to skip it. When I do plug it in, I get an error that only root can mount it so I use "storage mgr" to mount it, but in storage mgr, I see sda1 labelled as "elements" and sdb1 is also correctly labelled as "elements". If I try to manually change the label of sda1 (in storage mgr), it won't stay and reverts back to "elements". Because of this, I at one time, had several different labels for the partitions and drives in /media, so I removed all that didn't actually have anything in them, however, I still have two instances of each external drive in fstab.

On a maybe related point, I had to use a live USB to install 12.04 (also having issues with my internal DVD drive) and the install put grub somewhere (not sure where) and I had to use the usb flash drive to boot with until I manually installed grub to sda1.
So basically, how do I label all my partitions/drives, and how can I get 12.04 to correctly label them? 

info to follow

---

### Post by colin.p on 2012-05-17
I have it set up as follows: 

colin@colin-laptop:~$ sudo fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   356594804   178296378+  83  Linux
/dev/sda4       356594866   625137344   134271239+   5  Extended
/dev/sda5       356594868   401705324    22555228+  83  Linux
/dev/sda6       401705388   410637464     4466038+  82  Linux swap / Solaris
/dev/sda7       410637528   625137344   107249908+  83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907024895  1953511424    7  HPFS/NTFS/exFAT

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001    7  HPFS/NTFS/exFAT



colin@colin-laptop:~$ blkid

/dev/sda1: UUID="da6da247-0707-46c6-8c8e-c689a4166630" TYPE="ext4" 
/dev/sda5: LABEL="/" UUID="a8eedcb9-90b3-4d37-8697-ed8659de176b" TYPE="ext4" 
/dev/sda6: UUID="6bdddc06-c92b-48b1-8489-5b6c780729ab" TYPE="swap" 
/dev/sda7: LABEL="/home" UUID="87a80983-a6c2-4713-991b-a950c7c3c872" TYPE="ext4"

/dev/sdb1: LABEL="Elements" UUID="F07CFCEF7CFCB188" TYPE="ntfs" 
/dev/sdc1: LABEL="New Volume" UUID="400CE7C50CE7B3D6" TYPE="ntfs" 

My fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc     nodev,noexec,nosuid                       0  0  
#Entry for /dev/sda5 :
UUID=a8eedcb9-90b3-4d37-8697-ed8659de176b  /                 ext4     defaults                                  0  1  
#Entry for /dev/sda7 :
UUID=87a80983-a6c2-4713-991b-a950c7c3c872  /home             ext4     defaults                                  0  2  
#Entry for /dev/sdb1 :
UUID=F07CFCEF7CFCB188                      /media/Elements_  ntfs-3g  defaults,nosuid,nodev,locale=en_CA.UTF-8  0  0  
#Entry for /dev/sdc1 :
UUID=400CE7C50CE7B3D6                      /media/New Volume  ntfs-3g  defaults,nosuid,nodev,locale=en_CA.UTF-8      0  0  
#Entry for /dev/sda1 :
UUID=9d41aa13-5f9f-4f8d-8ae0-9a7c735d1707  /media/sda1       ext4     defaults,users-rw                         0  0  
#Entry for /dev/sda6 :
UUID=6bdddc06-c92b-48b1-8489-5b6c780729ab  none              swap     sw                                        0  0  

/dev/sda1                                  /media/sda1       ext4     defaults                                  0  0  
/dev/sdc1                                  /media/sdc1       ntfs     defaults,nosuid,nodev,locale=en_CA.UTF-8  0  0  

So if someone could direct me as to which direction I should go, I would be very grateful.

---

### Post by oldfred on 2012-05-17
You cannot have the space in 'New Volume'  in fstab.

I learned a while back to stop using spaces. Use CamelCase or under_score or just onename. Windows will work without the spaces and it makes things a lot simpler in Linux.

You can escape the space with this:
\040

New\040Home

I think you can also use quotes. But I would just change the mount location/name and mount under the new location/name.

sudo mkdir /media/NewVolume

Then use
UUID=400CE7C50CE7B3D6                      /media/NewVolume  ntfs-3g  defaults,nosuid,nodev,locale=en_CA.UTF-8      0  0

---

### Post by colin.p on 2012-05-17
I have used your suggestions as well as made some slight changes using the ntfs configuration tool and this is now my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=a8eedcb9-90b3-4d37-8697-ed8659de176b	/	ext4	defaults	0	1
#Entry for /dev/sda7 :
UUID=87a80983-a6c2-4713-991b-a950c7c3c872	/home	ext4	defaults	0	2
#Entry for /dev/sdb1 :
UUID=F07CFCEF7CFCB188	/media/Elements_	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=400CE7C50CE7B3D6	/media/New_Volume	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.UTF-8	0	0
#Entry for /dev/sda1
UUID=9d41aa13-5f9f-4f8d-8ae0-9a7c735d1707	/media/sda1	ext4	defaults	0	0
#Entry for /dev/sda6 :
UUID=6bdddc06-c92b-48b1-8489-5b6c780729ab	none	swap	sw	0	0


#UUID=9d41aa13-5f9f-4f8d-8ae0-9a7c735d1707	/media/sda1	ext4	defaults,users-rw	0	0
#/dev/sda1	/media/sda1	ext4	defaults	0	0

I have commented out the two seemingly superfluous listings for sda1 (the first one I created, the second I think storage mgr did). I am going into virgin territory here, but that's how I learn is by breaking things, then finding out how to fix them. Starting over from scratch probably would have been faster, but what's the fun in that?

Now both external drives seem to be working and listed properly, however, sda1 has to be manually mounted as I now get an error on booting up stating that sda1 is not ready and to press "s" to skip.
Any pointers on that? Also, I have some extra listings in /media, the ones with drive or USB inlays have stuff in them, the others don't. Is it ok to remove them? BTW, thanks very much for the prompt help.

[ATTACH]218165[/ATTACH]

---

### Post by oldfred on 2012-05-17
Does sda1 need e2fsck to repair something so it can mount. Or does the manual mount work ok?

Do you run this after editing fstab?

sudo mount -a

That verifies that everything is ok and remounts. No message is good.

If you want to know where every thing is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by colin.p on 2012-05-17
Thanks for your help and insight Fred, I think you nailed it. I, for some odd reason had the wrong UUID for sda1. When I typed "sudo mount -a"  it told me that the UUID was incorrect. So I changed it to what was in the boot script and (so far) all is well after a reboot. All drives appear and are behaving like they should.

So I should be good to go, at least until I break something, then I will be back for more pearls of wisdom.

---

