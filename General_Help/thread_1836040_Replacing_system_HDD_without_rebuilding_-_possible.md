---
title: "Replacing system HDD without rebuilding - possible?"
date: 2011-08-30
forum: General Help
---

### Post by zcacogp on 2011-08-30
Chaps, 

I'm hoping there is an easy answer to this - I cannot be the first person to have had this problem. 

I have a desktop machine running 11.04. The hard drive is failing. (At least, I think it is; it is producing some nasty SMART data and has just failed a self-test on account of 'read problems'.) There is only one HDD in the machine, which is split into partitions for 'system' and other things. 

I have ordered another HDD to replace it. It's not the same size, or the same brand, but it is SATA. Is there a way of copying data from the old HDD to the new one such that I don't have to rebuild my machine? 

Thanks, in advance, for your help. 


Oli.

---

### Post by seawolf167 on 2011-08-30
If the new hard drive is larger than or equal to the size of your current hard drive it couldn't be easier. Download a [Clonezilla ]("http://www.clonezilla.org")cd, burn to disk, pop it in your cd/dvd drive then follow the instructions to do a drive-to-drive copy. It'll even copy all the boot records, partition table, data, etc.

Once that has completed, remove your existing drive, replace with the new drive and everything will work just as it did before.

Now if your new drive is smaller its a bit harder but still do-able. Let us know and I can walk you through those steps.

---

### Post by zcacogp on 2011-08-30
Seawolf, 

Thanks - "Couldn't be easier" is the sort of answer I was hoping for! I'll download Clonezilla and see if I can have a play with it. 

Small snag is that the new disk is smaller than the old one (750Gb replacing 1Tb). Maybe you'll have to walk me through it. 

The new drive was ordered today, so I expect (hope) I'll be tackling this by the end of the week. 


Oli.

---

### Post by seawolf167 on 2011-08-30
> **zcacogp said:**
> Small snag is that the new disk is smaller than the old one (750Gb replacing 1Tb). Maybe you'll have to walk me through it. 

So now it gets a little complicated. It is ***MUCH*** easier (read: *child's play*) to do this if the disks are the same size (or the new one is larger).

If Ubuntu is the only operating system on your computer, download and burn a Ubuntu LiveCD (the standard install cd - 10.04.3 LTS).

Next, boot your computer off that cd and select the "Try Ubuntu" option to get to the desktop. From there, open GParted and ensure that you have your primary disk selected.

You now need to resize your partitions on the 1TB disk so that they all (added up) are less than the size of the new disk. Note that your 750GB disk actually has 698.625 GB of usable space.

Once the partitions have been re-sized, you'll need to transfer them to your new hard drive one at a time (without re-creating the existing partition table on the device). Once all the partitions have been transferred, you will need to reinstall Grub2 since you were not able to do a full drive image/transfer/disk-to-disk copy. There is a guide for that [here]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2").

Once that finishes and you are able to boot you'll need to ensure that your drive entries in /etc/fstab are correct and reflect the UUIDs of the drives after they have been resized.

---

### Post by rubylaser on 2011-08-30
This can done in Clonezilla as well.  Here are directions I used to transistion my server to a SSD.
[http://geekyprojects.com/storage/how-to-clone-hard-drive-to-smaller-drive/]("http://geekyprojects.com/storage/how-to-clone-hard-drive-to-smaller-drive/")

---

### Post by zcacogp on 2011-08-31
Seawolf, 

Thanks. I'll throw another spanner into those works; the machine is a dual-boot with XP as well. And there are some EXT3 partitions on the drive, and some NTFS ones too ... 

The new drive will hopefully arrive in the next day or so, and I'll come back and refer to the instructions that RubyLaser posted a link to. 

Having said that, the guide that RubyLaser linked to doesn't mention rebuilding GRUB ... is this an extra step that is necessary if you have a dual-boot machine? 

Thanks again for your help. And thanks RubyLaser for the link. 

I'll post back on here when I have the new drive in my sticky mitts. 


Oli.

---

### Post by seawolf167 on 2011-08-31
Clonezilla can handle any partition format type (NTFS, ext, fat, etc.) so no worries there. It'll just be more steps since you have more partitions to transfer over (or resize to ensure it fits on your new, smaller, disk)

Since it is a dual boot, you'll want to burn a Windows Recovery cd from your Windows installation before you begin. (You ***DID*** make a backup of your entire disk before you started right? Just incase something goes wrong). Put the Windows Recovery disk in the drive, boot off of it, and select to enter the recovery console. Once there, type in 

```
Bootrec.exe /RebuildBcd
Bootrec.exe /FixBoot
Bootrec.exe /FixMBR
```

Then, restart and ensure you can boot into Windows normally. Once you can do that, you'll need to put your Ubuntu LiveCD back in the drive and reinstall Grub2 following [these instructions]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2").

---

### Post by zcacogp on 2011-09-03
Chaps, 

Update: the new drive has arrived, and GParted is just shuffling the partitions around on the old drive prior to me getting stuck in with Clonezilla. 

Thanks for your help. I expect I will post again before the process is complete ... 

(GParted does seem to take some time; I presume this is normal? It did give a warning before I started that 'Moving partitions can take a LONG time' I guess it's just shuffling huge quantities of data across the surface of the disk.) 


Oli.

---

### Post by zcacogp on 2011-09-03
OK, this is getting a little more in-depth than I was hoping it would ... 

I used GParted to re-size everything on the old (larger) disk. It now looks like this: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot--dev-sda-GParted.png[/IMG]

I have put the CD with Clonezilla in the machine and booted from it. The boot sequence is interesting, but I get to pretty much the screens as described in the page linked to by rublaser (thanks RL). However, I believe I need to choose "device-device work directly from a disk or partition to a disk or partition" (I have both drives in the machine at the same time - both SATA.) 

I chose Beginner mode.

Then "disk_to_local_disk"

Then chose the source (bigger, Hitachi disk) 

Then chose the target (the only one in the list - the smaller, Samsung disk) 

It told me a command I can use directly next time I do this. (Helpful, but I hope I won't be doing this often!) 

It collected the information about the various partitions, and then gave me a warning about formatting the target disk. I said 'Y', and it asks whether create a partition on the target machine. Again, I said 'Y'. 

It then said (and I am copying from screen on another machine) 

```
Warning: partition 4 extends past end of disk. 

Successfully wrote the new partition table

Re-reading the partition table ...

....

Error: Can't have a partition outside the disk!
BLKRRPART: Device or resource busy
Checking the integrity of partition table in the disk /dev/sdb...
The partition table in this disk is illegal/invalid: /dev/sdb
Is this disk to small?
The error message from parted are:
************************************
Error: Can't have a partition outside the disk!
************************************
Program terminated!

```

To me, this looks like it doesn't like copying from larger to smaller, despite the fact that I re-sized everything so that there is a huge amount of spare space beyond the end of the last partition, and it should fit. 

What do I do now? 

All help welcomed - thanks. 


Oli.

---

### Post by seawolf167 on 2011-09-03
The problem here is that you selected the "disk to local disk" option. This is trying to take your entire existing [larger] hard disk and clone it to the smaller (note that it created the partition table for you too). You'll need to remove the partition table that was created with GParted and a Ubuntu LiveCD, then instead of doing "disc to local disk" you need to select to *move only partitions* and then only move them one at a time until you have them all transferred over. After this is finished, you'll install the Windows boot records to get it to boot, then install Grub2 as the MBR.

---

### Post by zcacogp on 2011-09-03
Seawolf, 

Thanks. I can see that that makes sense - I hadn't appreciated that disk-to-disk would fail; I thought it would work because there was enough spare space at the end of the source disk. Clearly not. 

I don't understand thy way that the Windows boot record records and GRUB interact, hence am a little shaky as to what precisely I am trying to do. (This is all a bit more involved than I was expecting! I am reassuring myself that if all fails, I can recover from back-ups onto the new disk, rebuilding both OS's if necessary. But I'd like to avoid this if I can.) 

OK, so to be clear, the steps I need to do are as follows (in order): 

1. Boot the machine with a live disk to remove the partition table from the new drive (which was created by my incorrect use of Clonezilla). (Not quite sure how I do this but I'll work it out.) 

2. Move individual partitions using Clonezilla, from the old disk to the new. (Will this create a correct partition table on the new disk?) 

3. Put a windows disk in the machine, boot to recovery console and enter the commands that you gave me in Post#7 of this thread. (This is the bit I don't understand). 

4. Rebuild GRUB, using the link you gave me also in Post#7. 

And then, all being well, I should be able to pull the plug on the old HDD and it will be ask it was when I started, but running on the new drive?

Thanks again for your help. I have a nasty feeling that I have bitten off a little more than I expected here, but I'll keep going ... 


Oli.

---

### Post by zcacogp on 2011-09-03
Small update as I go: when I booted into a live disk and looked at the new HDD, there were no partitions showing. Under 'device' I had the option to 'create partition table', so I am assuming that this means there is no partition table on the device? 

Continuing with step 2 ... 

Thanks again for your help. 


Oli.

---

### Post by seawolf167 on 2011-09-03
> **zcacogp said:**
> 1. Boot the machine with a live disk to remove the partition table from the new drive (which was created by my incorrect use of Clonezilla). (Not quite sure how I do this but I'll work it out.) 

Just delete any/alll partitions created yea, since all you are going to do is transfer each individual partition over to the new drive

> **zcacogp said:**
> 2. Move individual partitions using Clonezilla, from the old disk to the new. (Will this create a correct partition table on the new disk?) 

Yup, just move the partitions one at a time to the new disk. If clonezilla has problems creating the destination partitions, just create your own partition table on the device following the graphical output you posted earlier from GParted (as long as the destination partitions are larger than the existing partition sizes you'll be ok)

> **zcacogp said:**
> 3. Put a windows disk in the machine, boot to recovery console and enter the commands that you gave me in Post#7 of this thread. (This is the bit I don't understand). 

After all the partitions have been moved, boot off the Windows recovery cd and use those commands. Once done, you should be able to boot into only Windows without problems. Once Windows boots normally, proceed to #4 below

> **zcacogp said:**
> 4. Rebuild GRUB, using the link you gave me also in Post#7. 

Yes, install Grub2 as the MBR

> **zcacogp said:**
> And then, all being well, I should be able to pull the plug on the old HDD and it will be ask it was when I started, but running on the new drive?

Yup - I've done this same proceedure a couple times to move from my old[er] boot drives to new[er] SSD drives. Everything works perfectly.

> **zcacogp said:**
> Thanks again for your help. I have a nasty feeling that I have bitten off a little more than I expected here, but I'll keep going ... 

Unfortunately there are no native programs to do this to a smaller disk. Moving from a hard drive to one of the same size or larger just involves clicking "go!", no extra steps other than the first one you tried.

---

### Post by zcacogp on 2011-09-03
Seawolf, 

Thanks again. I think I am getting a bit of a handle on this ... 

I am struggling with a conceptual issue with Clonezilla; it appears to be creating clones of the partitions on the old HDD one by one, and asks for destinations for these clones. Key question: are these clones *the new partitions* (which need to be on the new HDD) or are they *the things that I will create the new partitions from?* Or, in other words, should I be telling it to place these clones on the new HDD (so effectively copying from one to the other, as a one-stage process), or should I be telling it to place these clones on some spare space on the old HDD, which would then require a second step of effectively "expanding" (there may be a better word) them onto the new HDD? 

Did that make sense? 


Oli.

---

### Post by owise1 on 2011-09-03
I had a similar problem - old HD (dual boot) started to play up - would take four or five goes to boot.  I removed that drive and replaced it with a larger drive and connected the old drive to one of those USB adaptors.  Then booted off live CD and did a 

dd if=/dev/sdb of=/dev/sda

Took overnight to complete.

Rebooted with no probs

---

### Post by zcacogp on 2011-09-03
owise1 - thanks. Sounds simpler than the route I seem to have embarked on! 

OK, from my previous question I think I understand the answer; it is certainly a 2-stage process, and I am creating things from the old drive that will later be restored to the new drive. 

That has presented me with a problem; where to place these things while the are 'in transit'. By my understanding, given that we are moving things chunk-by-chunk, the space on the drives can be used as I choose. On that basis I presumably can create a new partition in the large amount of free space I have created at the end of the old HDD, create all the cloned images in there, and then (later) re-create all of these on the new HDD. Is there any reason why this shouldn't work? 

Also, another (really elementary) question; why am I going to all this palaver; why can I not just copy the partitions from one drive to the other using 'copy', even from within Ubuntu (or using the live boot disk)?

(That may be a ridiculously daft question ... please be forgiving if it is!) 


Oli.

---

### Post by zcacogp on 2011-09-04
OK, We're making progress. I have clonedall the partitions except one using Clonezilla. And I have re-installed, from the clones created, the partitions on the new HDD. However I have two questions: 

1. Seawolf, you said "Since it is a dual boot, you'll want to burn a Windows Recovery cd from your Windows installation before you begin. (You DID make a backup of your entire disk before you started right? Just incase something goes wrong). Put the Windows Recovery disk in the drive, boot off of it, and select to enter the recovery console. " I created a Windows recovery CD using the instructions here: 

[http://createrecoverydisk.com/create-windows-xp-recovery-disk/](http://createrecoverydisk.com/create-windows-xp-recovery-disk/)

... which essentially involved going to Programs > Accessories > System Tools > Backup, and saving the backup image to the desktop then burning it to a CD. Is this what you meant by 'Create a windows recovery CD', or did you mean something else? 

2. The partition that failed to clone was the Ubuntu system partition. (I know that the old HDD had a lot of bad sectors, and I guess those bad sectors have prevented this bit from cloning. I tried it three times and each time it failed at 17%, so it's consistently duff if nothing else ... ) I'm not *that* upset by this as I can fairly easily re-build Ubuntu on the equivalent partition on the new HDD. However, what can I copy across from the old installation to the new one to save me time? For instance, I am sure I can copy the files to make the Samba shares work, and the keyboard shortcuts work, and the Compiz effects work and so on. Can I simply copy everything in /etc across? (Is this the point of /etc?) 

As always, all help welcomed, and thanks for getting me this far. 


Oli.

ETA: I have removed nothing from the old HDD yet, and if I just plug the old HDD into the machine - and not plug the new one in - then it boots exactly as it did before. So nothing lost at all ... yet.

ETA (again!): I tried running the commands given earlier on (namely: ```
Bootrec.exe /RebuildBcd
Bootrec.exe /FixBoot
Bootrec.exe /FixMBR
```

... in the Recovery Console from the original XP Installation CD (I have one), but it said that it didn't recognise the command Bootrec.exe. Not sure if this helps.

---

### Post by seawolf167 on 2011-09-04
1. Those commands were for Windows 7 (I just assumed thats what you were using), for XP, drop the "bootrec.exe" part & just use the xp install cd

```
fixboot c:
fixmbr c:
```

2. you can just straight-up copy everything across provided the destination partition is ext-formatted. make sure to do this from a livecd with root privileges so you have access to read/write all files.

---

### Post by zcacogp on 2011-09-04
Seawolf, 

Thanks again. I greatly appreciate the assistance you are giving me. 

It's moving along; I seem to have the partitions recreated on the new drive now (interestingly, Clonezilla didn't create the partition table - I had to do it using Gparted, as you suggested. Not that it was a major problem, but thanks for suggesting it.) 

I'm struggling with the creation of the MBR using the Windows disk. I'm not quite sure what is going on, but while I can run the commands you gave me (thanks for the updated versions), and it claims to execute them correctly, when I next try to boot it tells me "Error: file not found" and gives the prompt "Grub Recovery>". (Which strikes me as odd for two reasons; firstly why didn't it work?, and secondly where did it get GRUB from? I have yet to install GRUB on that disk ... )  

If I then re-try the XP disk to repeat the process then it doesn't find the Windows installation, and I have to re-create that partition from Clonezilla again. 

I've been 'round this loop twice now (I'm creating the partition for the third time), and am not sure how to get out of it. 

Any suggestions? 

I am aware that this is taking a lot of time; simply rebuilding both O/S's from scratch would have been quicker, but I am learning a lot in the process. (Which is good, I keep telling myself!) 

Thanks again. It's appreciated. 


Oli.

---

### Post by zcacogp on 2011-09-05
Update: I have re-installed GRUB (hoping that the above problem would be solved by doing so) and it hasn't; I now have a computer that boots (via GRUB, although the menu doesn't show) straight into Ubuntu, with no option to choose Windows. 

I'm googling to find the answer, but if anyone can help out then do let me know. 

Thanks. 


Oli.

---

### Post by YesWeCan on 2011-09-05
> **zcacogp said:**
> To me, this looks like it doesn't like copying from larger to smaller, despite the fact that I re-sized everything so that there is a huge amount of spare space beyond the end of the last partition, and it should fit. 

What do I do now? 
You need to shrink the extended partition too.

Then just clone the whole drive using dd:

sudo dd if=/dev/sdx of=/dev/sdy bs=64k conv=notrunc,noerror

where x is old drive, y is new drive. [COLOR="Red"]**This will erase everything on sdy**[/COLOR] so don't get the drive names mixed up!

Wait an hour or two.

When finished, disconnect the old drive and boot the new one. Dont have both drives connected at the same time or the boot loaders and fs mounters will get confused due to duplicated partition identifiers.

---

### Post by zcacogp on 2011-09-05
YesWeCan, 

Thanks .... I think I'm a little beyond that now (and am into windows-MBR-recreation-nightmares!) 

Thanks for your post though. 


Oli.

---

### Post by YesWeCan on 2011-09-05
It may be a lot easier to start from scratch. :)

If you have disconnected your original drive and can boot Into Ubuntu on the new one, then run
[COLOR="Navy"]sudo update-grub[/COLOR]
This should detect the Windows OS and add it to the boot menu.
If this does not work Id start from scratch. Its just easier.

---

### Post by zcacogp on 2011-09-05
YWC, 

I have a nasty feeling you are right - it would be easier to start from scratch! 

Updating GRUB doesn't seem to work. I have just had to re-install UBUNTU on the second partition (don't ask why!) and that rebuilt GRUB in the process. It now boots nicely to Ubuntu, but didn't recover Windows. 

One question; I notice that I can set a flag on a partition as being "Bootable". Does the Windows partition have to have this flag set? 


Oli.

---

### Post by YesWeCan on 2011-09-05
Normally, your disk partitions would be booted by MBR code which chooses which one to boot according to the boot flag. This is how Windows works.

Ubuntu does not work with the MBR system. So it replaces it! Grub replaces the normal MBR boot code and ignores the boot flag.

It may be fixable as is but it is very difficult to see what is going on with your new disk without using bootinfoscript. Would you download this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and run it and post RESULTS.txt in code tags (highlight and click # above)?



**It is essential that the original disk is not connected.**

---

### Post by zcacogp on 2011-09-05
YWC, 

Many thanks - I'll do that right away. 

Back in a mo. 


Oli.

---

### Post by zcacogp on 2011-09-05
OK, results here. (To my - untrained - eye they look interesting. I'm sure others will be able to make more sense of them.) 

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 662480896. But according to the info from 
                       fdisk, sda7 starts at sector 669704192.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465147055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   125,954,047   125,952,000   7 NTFS / exFAT / HPFS
/dev/sda2    *    125,954,048   332,802,047   206,848,000  83 Linux
/dev/sda3         332,802,048   342,018,047     9,216,000  82 Linux swap / Solaris
/dev/sda4         342,020,094   772,104,191   430,084,098   5 Extended
/dev/sda5         342,020,096   536,580,095   194,560,000  83 Linux
/dev/sda6         536,582,144   669,702,143   133,120,000  83 Linux
/dev/sda7         669,704,192   772,104,191   102,400,000   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A014987414984F62                       ntfs       
/dev/sda2        f49dfdd1-4210-4cf7-bcc8-2d35837aa604   ext3       
/dev/sda3        0f5258c0-052b-4956-8674-d45d4b298639   swap       
/dev/sda5        1d588936-4308-4e8d-9ad8-9c0ba6cf118f   ext4       Helena
/dev/sda6        728c678a-4bf6-4c78-8cb2-30b61d9be26f   ext4       Ianthe
/dev/sda7        52C399D625D0301D                       ntfs       Pharmacy

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=f49dfdd1-4210-4cf7-bcc8-2d35837aa604 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=f49dfdd1-4210-4cf7-bcc8-2d35837aa604 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f49dfdd1-4210-4cf7-bcc8-2d35837aa604 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f49dfdd1-4210-4cf7-bcc8-2d35837aa604 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root f49dfdd1-4210-4cf7-bcc8-2d35837aa604
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=0f5258c0-052b-4956-8674-d45d4b298639 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 115.208118439 = 123.703775232  boot/grub/core.img                             1
 115.215965271 = 123.712200704  boot/grub/grub.cfg                             1
 115.229804993 = 123.727060992  boot/initrd.img-2.6.38-11-generic              8
 115.204853058 = 123.700269056  boot/initrd.img-2.6.38-8-generic               6
 115.267017365 = 123.767017472  boot/vmlinuz-2.6.38-11-generic                 3
 115.293979645 = 123.795968000  boot/vmlinuz-2.6.38-8-generic                  3
 115.229804993 = 123.727060992  initrd.img                                     8
 115.204853058 = 123.700269056  initrd.img.old                                 6
 115.267017365 = 123.767017472  vmlinuz                                        3
 115.293979645 = 123.795968000  vmlinuz.old                                    3

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

OK, I'm a beginner at this sort of thing, but correct me if my logic is wrong; Under sda1, the report says that the boot sector thinks that sda1 starts at sector 63, but fdisk thinks it starts from sector 2048. 

Having checked with GParted, sda1 does indeed start at sector 2048 (which is apparently the earliest it can start - I tried moving it forwards to an earlier sector and it wasn't allowed.) 

Surely this can explain the problem; the boot sector is aiming at a false target, which is sector 63. If I can edit the boot sector to tell it to aim at 2048 instead of 63 then all will be well. 

Is this a correct summary? 

If it is then how do I edit the boot sector? (If it isn't then where have I gone wrong? :) ) 

I notice there is a similar problem later on, with sda7 (incidentally the only other NTFS partition on the disk). This has the following note: *According to the info in the boot sector, sda7 starts at sector 662480896. But according to the info from fdisk, sda7 starts at sector 669704192."* The offset error is much bigger but the problem is the same. Is there a common issue, and if so, what is it?

Thanks again for your help. 


Oli.  

Oli.

---

### Post by YesWeCan on 2011-09-05
The problem with Windows is that its partition boot code in sda1 thinks sda1 starts at sector 63 whereas it starts at 2048. This will break Windows boot. Something must have changed it when you cloned the disk.

If you have a Windows XP installation CD you should boot it and select repair and do fixboot (or whatever it is called).

But first, set the boot flag to sda1 or the XP repair wont work.

[COLOR="Navy"]sudo sfdisk -A1 /dev/sda[/COLOR]


Then there is a potential problem (not related to your current one but could cause trouble in the future) in /etc/fstab because it uses a /dev/sda2 reference for / rather than a UUID reference. It should look like this instead:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                               <mount point>      <type>   <options>              <dump>  <pass>

proc                                              /proc           proc    nodev,noexec,nosuid      0       0

UUID=f49dfdd1-4210-4cf7-bcc8-2d35837aa604         /               ext3    errors=remount-ro        0       1

UUID=0f5258c0-052b-4956-8674-d45d4b298639         none            swap    sw                       0       0
```

---

### Post by zcacogp on 2011-09-05
YesWeCan, 

OK, this is feeling promising. Thank you. 

I have done fixboot several times, along with fixmbr (should I do both, or just the one? I thought it was both), but never set the flag on sda1 to bootable (see my comments above.) 

I put in the command you suggested and had this result: 
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Done

```Likely to cause a problem? 

I'll spin up the XP disk now, run fixboot and fixmbr (unless you think I should only do fixboot) and see where that leaves us. 

Thanks again for your help. I'll post results on here in a moment. 


Oli.

ETA: I noticed the lack of UUID in fstab - easily enough fixable. But thanks for pointing it out to me.

---

### Post by YesWeCan on 2011-09-05
> **zcacogp said:**
> OK, I'm a beginner at this sort of thing, but correct me if my logic is wrong; Under sda1, the report says that the boot sector thinks that sda1 starts at sector 63, but fdisk thinks it starts from sector 2048. 

Having checked with GParted, sda1 does indeed start at sector 2048 (which is apparently the earliest it can start - I tried moving it forwards to an earlier sector and it wasn't allowed.) 

Surely this can explain the problem; the boot sector is aiming at a false target, which is sector 63. If I can edit the boot sector to tell it to aim at 2048 instead of 63 then all will be well. 

Is this a correct summary? 

If it is then how do I edit the boot sector? (If it isn't then where have I gone wrong? :) ) 
Spot on! I think Clonezilla got carried away. Editing the partition boot code to change the target from 63 to 2048 is non-trivial. You'd have to modify things at the byte level and know where all of the boot code addresses are located. Very challenging! Much easier to start from scratch. ;)

> I notice there is a similar problem later on, with sda7 (incidentally the only other NTFS partition on the disk). This has the following note: *According to the info in the boot sector, sda7 starts at sector 662480896. But according to the info from fdisk, sda7 starts at sector 669704192."* The offset error is much bigger but the problem is the same. Is there a common issue, and if so, what is it?
Similar sort of unwanted relocation. This may be ok because this is a data partition and will not be booted. You should probably run a chdsk on it once XP is running.

---

### Post by YesWeCan on 2011-09-05
> **zcacogp said:**
> Likely to cause a problem?
I don't think so. This warning crops up a lot these days. I think in olde times it mattered but nowadays "cylinder" boundaries are not important.

---

### Post by YesWeCan on 2011-09-05
> **zcacogp said:**
> I'll spin up the XP disk now, run fixboot and fixmbr (unless you think I should only do fixboot) and see where that leaves us.
For good measure I'd do both and get XP booting on its own properly. Check your Windows drives are ok. Run check disk on the last one. I'm not an expert on Windows partitions so I'm sort of making this up. But just make sure it is happy and all your files are accessible.

Then reboot off Ubuntu live CD and reinstall Grub:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Then reboot into Ubuntu and run
```
sudo update-grub
```
to add XP to the boot menu.

BTW your sda2 is ext3 not ext4?

---

### Post by zcacogp on 2011-09-05
YWC, 

OK, I've tried as you suggested. It appeared to work, but the machine still boots to GRUB and then straight through to Ubuntu. No change. 

I suspect I have simply repeated what I did before and which I described in Post#14 of this thread, namely: 

[quote=zcacogp]

I'm struggling with the creation of the MBR using the Windows disk. I'm not quite sure what is going on, but while I can run the commands you gave me (thanks for the updated versions), and it claims to execute them correctly, when I next try to boot it tells me "Error: file not found" and gives the prompt "Grub Recovery>". (Which strikes me as odd for two reasons; firstly why didn't it work?, and secondly where did it get GRUB from? I have yet to install GRUB on that disk ... )

If I then re-try the XP disk to repeat the process then it doesn't find the Windows installation, and I have to re-create that partition from Clonezilla again.

I've been 'round this loop twice now (I'm creating the partition for the third time), and am not sure how to get out of it. [/quote]

I have also just run the boot_info_script again and it gives this result: 

```
sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```



Oli.

---

### Post by zcacogp on 2011-09-05
> **YesWeCan said:**
> For good measure I'd do both and get XP booting on its own properly. Check your Windows drives are ok. Run check disk on the last one. I'm not an expert on Windows partitions so I'm sort of making this up. But just make sure it is happy and all your files are accessible.
I haven't checked them but have no reason to think that the windows drives aren't OK. Good suggestion tho'. 

> **YesWeCan said:**
> 
Then reboot off Ubuntu live CD and reinstall Grub:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Then reboot into Ubuntu and run
```
sudo update-grub
```
to add XP to the boot menu.

It is still booting through GRUB as the re-build of the MBR in Windows wasn't successful. (As I understand it, if the re-build of the MRB in Windows had been successful then it would now boot straight into Windows. Because it wasn't, it still boots into GRUB)

> **YesWeCan said:**
> BTW your sda2 is ext3 not ext4?Yes; for some reason my machine has had problems historically running a Ubuntu system drive with EXT4. I don't know why, but cutting back to EXT3 makes it happy again.

Thanks again for your help. I would say that I have the ultimate silver bullet in simply re-installing Windows, but if using the Command Console can't repair the MBR then I am starting to doubt whether it would do any better if I did do a full re-install. (Which I'd like to avoid anyway!) 


Oli.

---

### Post by YesWeCan on 2011-09-05
It looks like even XP can't repair the damage. :(

You can reinstall XP from scratch or

Reclone the disk as per post #21.


Good luck with it. :)

---

### Post by zcacogp on 2011-09-05
YWC, 

I think you are right - the nuclear option is about the only way now. Re-build from scratch! 

Very, very annoying; this is exactly what I was trying to avoid by being clever with Clonzilla! And I still can't quite understand what went wrong ... 

Thanks very much for your help though. It really was appreciated. 


Oli.

---

### Post by YesWeCan on 2011-09-05
Don't forget to use GParted to shrink the extended partition on your original disk first and disconnect the original before you try to boot the new one.

---

### Post by zcacogp on 2011-09-05
YesWeCan, 

No - I've tried re-cloning and installing the new clone (only of the affected partition); it just gets back to the same place with no clear way forwards. 

As I type this I am doing a clean install of XP from the XP CD. 'Tis a pain, but if anything will work it should be this. (Although I'll be utterly scuppered if it doesn't!) 

I know that I'll have to update GRUB if it does work. 


Oli.

---

### Post by YesWeCan on 2011-09-05
You can't just clone one partition and expect it to work.

You have to clone the whole drive. That way the MBR and partition table get cloned, the boot-loaders get cloned, all the partitions are in the right place, all your files and links are intact.

---

### Post by zcacogp on 2011-09-05
Oh. In which case I have been wasting your time (and my time too) - many apologies. 

Would I ever have had a chance of making it work using Clonezilla? (Given that I am moving from a larger to a smaller disk). What extra steps should I have taken to create the MBR? I thought that was the thing that would have been re-created from the XP Recovery Console? 

I created the partition table manually in GParted, as a copy of the one on the old HDD. 

Was I always on a hiding to nothing? 


Oli.

---

### Post by YesWeCan on 2011-09-05
Don't apologize - it's all learning for everybody! :)
My mistake. I thought you had tried to clone the entire disk. Cloning one partition at a time is much more time consuming and trickier.

That would explain how XP ended up at sector 2048 instead of 63.

Why not just clone the whole disk? Is there something on the 750GB that was not on the original disk that you need to keep? The dd command in post #21 will erase your new disk.


I suppose,
To clone just XP you would probably have to make a partition on the 750GB drive in exactly the same place as the original, eg: starting at sector 63, and ending at the right sector, and then dd the partition only and then set the boot flag and then try to boot. But it might or might not depending on whether it cares about the partition UUID or not. So a repair might be needed or a chkdsk or something. It is essential that the cloned partition is in exactly the same place on the new drive.

---

### Post by zcacogp on 2011-09-05
YWC, 

I couldn't clone the whole disk as the new disk is smaller than the old one. Quarts into pint pots and all that ... 

I cloned each partition in turn and re-created them in the manually-made partition table on the new machine. The new disk was blank when I started. 

Learning ... yes, I guess so. Although I wish I had known more before I started on this particular road ... :(


Oli.

---

### Post by YesWeCan on 2011-09-05
> **zcacogp said:**
> I couldn't clone the whole disk as the new disk is smaller than the old one. Quarts into pint pots and all that ... 
Not a problem as long as the used space on the original - from start to end of last partition is smaller than the new disk.
Here I am cloning an 10GB drive to a 5GB drive, the used space on the 8GB is <5GB:
Before:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     4280319     2139136    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2         4280320    10422271     3070976   83  Linux
Partition 2 does not end on cylinder boundary.

Disk /dev/sdj: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders, total 10485760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098043

   Device Boot      Start         End      Blocks   Id  System
```Then clone
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdj bs=64k conv=notrunc,noerror
dd: writing `/dev/sdj': No space left on device
81921+0 records in
81920+0 records out
5368709120 bytes (5.4 GB) copied, 14.1638 s, 379 MB/s

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sd[aj]

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     4280319     2139136    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2         4280320    10422271     3070976   83  Linux
Partition 2 does not end on cylinder boundary.

Disk /dev/sdj: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders, total 10485760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048     4280319     2139136    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdj2         4280320    10422271     3070976   83  Linux
Partition 2 does not end on cylinder boundary.

ubuntu@ubuntu:~$ sudo hdparm -z /dev/sdj

/dev/sdj:
 re-reading partition table

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="5198D9A46C91DA0E" TYPE="ntfs" 
/dev/sda2: UUID="c84f9197-12f6-4a10-89a1-78c29d723ce7" TYPE="ext4" 
/dev/sdj1: UUID="5198D9A46C91DA0E" TYPE="ntfs" 
/dev/sdj2: UUID="c84f9197-12f6-4a10-89a1-78c29d723ce7" TYPE="ext4" 

ubuntu@ubuntu:~$ 
```

---

### Post by zcacogp on 2011-09-05
In which case ... I wish you'd seen (and replied to) this thread a couple of days ago! :)

Thanks anyway - good to know that such things are possible. I've bookmarked this thread for future reference. 


Oli.

---

