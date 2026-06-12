---
title: "ubuntu won't start anymore after power outage."
date: 2011-05-25
forum: General Help
---

### Post by blabla1 on 2011-05-25
I was watching a movie, and the power went off and the laptop shut off because my battery is dead.

When i tried to start it again, i went in the boot menu choose ubuntu, nothing happens.
I tried recovery mode. It started doing stuff, then in the end i got:

(I installed ubuntu through wubi btw)

mount: mounting /dev/loop0 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed
: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init = bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) buildt-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_

----------------------------------------
Any help would be appreciated to get it to work properly again

---

### Post by spikoley on 2011-05-25
Try booting into the live CD and then reboot into your install.  I has a similar issue one time and this worked.  I was just trying to recover files, but for some unknown reason when I reboot it worked.  Its worth a shot.

---

### Post by blabla1 on 2011-05-25
Ok. I don't have a live CD BUT i have copied the live CD from a friend on my external HDD into a folder a while back, but i don't know how to boot it from the external... I'm a bit of a newb at this... :P

when i try it gives me:
-----------------------------
PXE-E61: Media test failure, check cable
PXE-MOF: Exiting PXE ROM.
Invalid partition table

--------------------------

The cable is fine btw.

---

### Post by spikoley on 2011-05-25
> **blabla1 said:**
> Ok. I don't have a live CD BUT i have copied the live CD from a friend on my external HDD into a folder a while back, but i don't know how to boot it from the external... I'm a bit of a newb at this... :P

when i try it gives me:
-----------------------------
PXE-E61: Media test failure, check cable
PXE-MOF: Exiting PXE ROM.
Invalid partition table

--------------------------

The cable is fine btw.

You have to install it onto the external drive.  Just coping it over won't work.

---

### Post by Rubi1200 on 2011-05-25
Is Windows booting normally?

When you choose Ubuntu and you see the first screen is there a menu with different kernels?

If yes, pick the first one and press "c".

This will bring you to a grub> prompt.

At the prompt, type ls.

Post the output here please.

---

### Post by wgarcia on 2011-05-25
You need to run fsck over your linux install. You have to do this without having the disks mounted, so the best is doing from a live USB or CD session. 

The steps would be the following:

1. Start from a CD or USB Live Ubuntu

2. Open a terminal (Applications -> Terminal, or SuperKey -> Terminal in Unity)

3. Enter: sudo fdisk -l
(this will tell you the name of the partition where your Linux install lives)

For instance you could get:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: **********

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30238 242886703+ 83 Linux
/dev/sda2 30239 30401 1309297+ 5 Extended
/dev/sda5 30239 30401 1309266 82 Linux swap / Solaris

The name would be  /dev/sda1 in this case


4. Enter: sudo fsck /dev/sda1
5. Reboot and see if it starts normally.

---

### Post by blabla1 on 2011-05-25
> **Rubi1200 said:**
> Is Windows booting normally?

When you choose Ubuntu and you see the first screen is there a menu with different kernels?

If yes, pick the first one and press "c".

This will bring you to a grub> prompt.

At the prompt, type ls.

Post the output here please.

Yes windows is booting normally.
I typed ls and got:

(memdisk) (loop0) (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)


@[wgarcia]("http://ubuntuforums.org/member.php?u=242060") 

I don't have a live CD or a live USB

---

### Post by Rubi1200 on 2011-05-25
Okay, blabla1 you need to understand a few things. If the procedure I give you now does not work, you must somehow get hold of a LiveCD.

Chances are the file-system is damaged and requires a file-system check. This can only be done from the LiveCD as far as I know.

So, to try and boot the Wubi install you also need to figure out which is the Windows partition from the list of partitions you posted the output for.

It is will be one of these 3:
> (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

Run these commands at the grub prompt you now know how to access:

```
set root=(hdX,Y)  # Example: (hd0,1) , (hd1,5)
loopback (loop0) /ubuntu/disks/root.disk
set root=(loop0)[/B]
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro  # Example: root=/dev/sda1 , /dev/sdb5
initrd /initrd.img
boot
```

Anything after the # is just an example, change as needs be. By the way, for the commands this hd0,msdos3 = this hd0,3

If all of this gets you booting into Ubuntu, run ```
sudo update-grub
``` afterwards.

If not, as I said before you need to get hold of a LiveCD and then we can take it from there.

Good luck!

---

### Post by blabla1 on 2011-05-25
> **Rubi1200 said:**
> Okay, blabla1 you need to understand a few things. If the procedure I give you now does not work, you must somehow get hold of a LiveCD.

Chances are the file-system is damaged and requires a file-system check. This can only be done from the LiveCD as far as I know.

So, to try and boot the Wubi install you also need to figure out which is the Windows partition from the list of partitions you posted the output for.

It is will be one of these 3:


Run these commands at the grub prompt you now know how to access:

```
set root=(hdX,Y)  # Example: (hd0,1) , (hd1,5)
loopback (loop0) /ubuntu/disks/root.disk
set root=(loop0)[/B]
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro  # Example: root=/dev/sda1 , /dev/sdb5
initrd /initrd.img
boot
```Anything after the # is just an example, change as needs be. By the way, for the commands this hd0,msdos3 = this hd0,3

If all of this gets you booting into Ubuntu, run ```
sudo update-grub
``` afterwards.

If not, as I said before you need to get hold of a LiveCD and then we can take it from there.

Good luck!

when i type:
set root=(hd0,1) it gives me error: not an assignment.

---

### Post by Rubi1200 on 2011-05-25
Try with hd0,2 and hd0,3 and let me know what happens.

Meantime, here is the link for downloading Ubuntu. There are also instructions on the page on how to create a LiveCD and boot the computer with it.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I suggest you download the 10.04 version (available from the drop-down menu).

---

### Post by blabla1 on 2011-05-25
I get the same error:
error: not an assignment.


And I won't be able to download it now since it takes about 6-7hours to download about 700MB with my internet connection (Yes, I know it's very slow but this is what's available in the country i live in :P). And i can't start before 11pm, so I'll be back tomorrow with the live CD hopefully. I hope you check this thread again tomorrow.

---

### Post by Rubi1200 on 2011-05-25
> **blabla1 said:**
> I get the same error:
error: not an assignment.


And I won't be able to download it now since it takes about 6-7hours to download about 700MB with my internet connection (Yes, I know it's very slow but this is what's available in the country i live in :P). And i can't start before 11pm, so I'll be back tomorrow with the live CD hopefully. I hope you check this thread again tomorrow.
I suspect the errors are because of damage to the file-system.

Make sure you burn the image at the slowest possible speed for best results.

I will keep an eye on the thread and will definitely be back to help you.

---

### Post by blabla1 on 2011-05-27
[SIZE=3]Here's the result:
  [/SIZE]```
[SIZE=3]Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   198,434,815   195,360,768   7 NTFS / exFAT / HPFS
/dev/sda3         198,434,816   390,721,535   192,286,720   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        40EC604FEC6040F0                       ntfs       WinRE
/dev/sda2        6C600E14600DE624                       ntfs       
/dev/sda3        0892668792667958                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /tmp/BootInfo0/sda2      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
[/SIZE]
```

---

### Post by Rubi1200 on 2011-05-27
Hi and thanks for posting the results.

I am a bit concerned because it appears part of the results are missing and I see no evidence of a Wubi install.

If you look at the root of the C drive do you see any Ubuntu folders at all and if yes what files are in there?

---

### Post by blabla1 on 2011-05-27
erm do you mean in the Computer>File System>Root ?

if yes i typed gksudo nautilus to open it and only found Desktop

---

### Post by Rubi1200 on 2011-05-27
Hi,

boot back into Windows and enable the option to see hidden files and folders. Then look for a folder called C:\found.000 or similar.

Use the advanced search in Windows and see if you find any of the Wubi files because even though we have seen cases where the root.disk becomes damaged as a result of what you described it would be very odd if _all_ the files were gone.

---

### Post by blabla1 on 2011-05-27
In C the ubuntu folder is still there and has: Disks, install, winboot, ubuntu, and uninstall-wubi in it

---

### Post by Rubi1200 on 2011-05-27
Okay, what is inside the disks folder?

---

### Post by blabla1 on 2011-05-27
There is a boot folder, a root.disk and a swap.disk file

---

### Post by Rubi1200 on 2011-05-27
Okay, the error you originally posted indicates possible damage to the file-system.

This is what I suggest; boot the computer with the LiveCD again choosing to try not install.

Then open a terminal and run these commands:

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```When the last command is finished, run this command to mount the Wubi install:

```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```If everything was successful, the root.disk should mount and you can access your data.

Then reboot taking out the CD and you should be able to access Ubuntu normally from the menu where you usually choose to start it.

If this seems a bit much, then copy the root.disk to a safe place like another USB stick just in case something goes wrong.

Let me know what happens or if you encounter any problems.

---

### Post by blabla1 on 2011-05-27
I got an error:


ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/win
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/media/win/ubuntu/disks/root.disk: recovering journal
Error reading block 1612557 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>?

There's only one choice :P yes...
but i want to be careful so I'm asking...

---

### Post by Rubi1200 on 2011-05-27
Did you make a backup of the root.disk as I suggested?

It should be okay to go ahead and answer yes, but I don't want you losing data so if you are at all unsure first backup the root.disk and then do this. By the way, you may have to answer yes a few more times as well because you are running fsck without any arguments. This is normal.

We can always restore the original root.disk if this doesn't work.

---

### Post by blabla1 on 2011-05-27
Tried to go to ubuntu.

Got a box that said could not update ICEauthority file var/lib/gdm/.ICEautority
I pressed Close
I got another box saying: There is a problem with the configuration server (usr/lib/libconf2-4/gconf-sanity-check-2existed with status 256)
I pressed Close

I got that Gnome something something wasn't installed correctly something something in a box on the top right and the normal ubuntu login page showed up but with messed up colors and stuff. I put the password in. Nothing happened. I restarted tried to get in again and i got the same thing that i got the first time in my first post in this thread.

I guess it's hopeless...

---

### Post by Rubi1200 on 2011-05-27
Nothing is hopeless, at least not yet. Also, I don't give up easily. I will try and help you until we have run out of options, which I hope won't be the case.

So, here is what you need to do please.

Boot back into Windows and run a chkdsk:
[http://www.winvistatips.com/vista-chkdsk-t126028.html](http://www.winvistatips.com/vista-chkdsk-t126028.html)

This has pictures, always nice; make sure you also check the option to scan for and attempt recovery of bad sectors.

You will need to restart the computer and then go have a coffee or something because it might take some time.

Once it is finished boot back into Windows and make sure everything is okay with Windows.

You can also check to make sure the disks folder and contents are still there.

If Windows reports errors, you may need to run chkdsk a few times until there are no more errors.

So, take a deep breath. Now, after all that is done, you need to run the LiveCD again and try the boot script and posting the results.

It is possible that the reason we didn't see the whole results before was because of a problem on the Windows side in addition to the Wubi issue.

Anyway, I will keep an eye on things and you are welcome to send me a message again if I go offline.

Good luck!

---

### Post by blabla1 on 2011-05-27
I ran chdsk twice, and it didn't report any errors when i logged in to windows and everything looked fine.
If the errors were reported while the process was running i might have no seen them because i wasn't near my laptop the whole time but i doubt it's the case here.

So i ran that script again after booting from a live CD and the same results came up like last time.

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   198,434,815   195,360,768   7 NTFS / exFAT / HPFS
/dev/sda3         198,434,816   390,721,535   192,286,720   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        40EC604FEC6040F0                       ntfs       WinRE
/dev/sda2        6C600E14600DE624                       ntfs       
/dev/sda3        0892668792667958                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /tmp/BootInfo0/sda2      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by Rubi1200 on 2011-05-28
Hmm, this is odd.

Just out of curiosity, let's run an older version of the boot script so we can rule out a problem with that aspect.

As before, use the LiveCD and go to the site but instead of downloading the latest version look under other versions and download the 055 version.

Then run this command:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
Post the results again.

Thanks for being so patient about this.

---

### Post by blabla1 on 2011-05-28
No Thank YOU for being so patient :P

And this time the results were different. Hopefully this is good.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   198,434,815   195,360,768   7 HPFS/NTFS
/dev/sda3         198,434,816   390,721,535   192,286,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       68d07c26-97cb-4442-b28c-da705705b72a   ext4                                     
/dev/sda1        40EC604FEC6040F0                       ntfs       WinRE                         
/dev/sda2        6C600E14600DE624                       ntfs                                     
/dev/sda3        0892668792667958                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by Rubi1200 on 2011-05-28
Well, this is interesting. These results are what I would have expected to see in the first place. 

So, as we know there is damage to the filesystem.

Let's run another check and see if something changes:

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo e2fsck -f -y -v /media/win/ubuntu/disks/root.disk
```

If this causes problems (because I changed the parameters for the fsck) then just do a plain fsck as before.

Reboot and see if you are back in Ubuntu.

If none of this works, then I will send a message to bcbc, forum member and Wubi expert, asking him to also offer some ideas of how we can work this out.

You may have to wait though because of time-zone differences.

Thanks.

---

### Post by blabla1 on 2011-05-28
:D :D :D
IT WORKS!!1!!! lol
Thank you very very much for your help.

---

### Post by Rubi1200 on 2011-05-28
> **blabla1 said:**
> :D :D :D
IT WORKS!!1!!! lol
Thank you very very much for your help.
Excellent! This is great news :D

Okay, we are not quite done yet. This time run the boot info script from _within_ Ubuntu and post the results.

I want to check if there are any additional changes you need to apply in light of what happened.

But, assuming we are all set you can mark this Solved using the Thread Tools near the top of the page.

Keep the LiveCD handy as you never know when you might need it again for repair work.

---

### Post by blabla1 on 2011-05-28
Alright.

Oh and now that i have all the files again I'm backing everything up and I'll be installing ubuntu normally in a couple of days(not through wubi) and uninstalling the wubi one to avoid problems like this in the future.

Here's the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   198,434,815   195,360,768   7 HPFS/NTFS
/dev/sda3         198,434,816   390,721,535   192,286,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       68d07c26-97cb-4442-b28c-da705705b72a   ext4                                     
/dev/sda1        40EC604FEC6040F0                       ntfs       WinRE                         
/dev/sda2        6C600E14600DE624                       ntfs                                     
/dev/sda3        0892668792667958                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-24-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, Linux 2.6.35-24-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6c600e14600de624
    chainloader +1
}
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

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   1.5GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
   1.1GB: boot/initrd.img-2.6.35-24-generic
   8.4GB: boot/initrd.img-2.6.35-25-generic
   3.6GB: boot/initrd.img-2.6.35-27-generic
   5.5GB: boot/initrd.img-2.6.35-28-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
  11.0GB: boot/vmlinuz-2.6.35-24-generic
  11.0GB: boot/vmlinuz-2.6.35-25-generic
  15.1GB: boot/vmlinuz-2.6.35-27-generic
   4.4GB: boot/vmlinuz-2.6.35-28-generic
   5.5GB: initrd.img
   3.6GB: initrd.img.old
   4.4GB: vmlinuz
  15.1GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2011-05-28
Ah, if you are planning on an install to the hard-drive anyway then there is probably no point doing what I would have suggested.

However, here are some tips and tricks for safe dual-booting.

1. backups, backups, backups including creating Windows recovery disks:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

2. great partitioning and installation guide: [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

3. more useful information:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Good luck and let me know if you need more help with anything in the future.

---

### Post by blabla1 on 2011-05-28
Thanks again for all your help :)

---

### Post by Gert Hulselmans on 2011-05-31
@ blabla1
From which live CD did you run Boot Info Script v0.60?

Can you mount partition sda2 and copy the grldr file to your home directory?

Then run:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null | hexdump -v -e '/1 "%02x"' | grep -b -o 'b0021ace000000000000000000000000'
```If it produces any output, post it.

Else, try:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | less
```(press 'q' to quit)

If this showed, you a lot of hexadecimal characters, try the following:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null | hexdump -v -e '/1 "%02x"' | grep -b -o '47524c4452'
```And post the output.

---

