---
title: "restoring 10.04 boot"
date: 2011-01-04
forum: General Help
---

### Post by wcutrombonekid on 2011-01-04
So, I broke my ubuntu partition a while back.  I let it sit there and die, so it did a hard shut down and now it wont boot.  Basically this whole semester I've been using vista because its the only other OS I have and I haven't had time to try and fix it.  
I've played around and can't seem to understand what to do to get it back.  I've searched forums and nothing seems to help.

It is 10.04 so if I fix it, I will just upgrade it to 10.10

I was wondering if any one knew what to do.

When I start my computer, I get a black screen after it goes through grub that says this:

"target filesystem doesn't have /sbin/init"

theres also a bunch of lines of what I think is it trying to mount the partition, but it can't.

does anyone know what I need to do to get my computer back?  theres a lot of information on there that I need to get

thanks 
chris

---

### Post by wcutrombonekid on 2011-01-05
bump

help please!

---

### Post by wcutrombonekid on 2011-01-21
last bump.  if you know anything let me know.  I really need help

---

### Post by Rubi1200 on 2011-01-21
Hi,
this is what you need to do please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once you post the results, I will try and help as best I can.

---

### Post by tredegar on 2011-01-21
Boot from a live CD
Then try and mount your HDD (it should be listed under "Places") and navigate to your home directory.
Copy the files to an external USB HDD

---

### Post by wcutrombonekid on 2011-01-21
awesome, thanks guys.  I'll do this tonight, i'm busy untill later, i'll hopefully have results by midnight.  

thanks guys, I appreciate it

---

### Post by wcutrombonekid on 2011-01-22
There you go, thanks again

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    16,787,924    16,787,862   7 HPFS/NTFS
/dev/sda2         294,857,010   625,137,344   330,280,335   7 HPFS/NTFS
/dev/sda3          21,318,255   294,857,009   273,538,755   5 Extended
/dev/sda5         280,461,312   294,133,759    13,672,448  83 Linux
/dev/sda6         294,135,808   294,856,703       720,896  82 Linux swap / Solaris
/dev/sda7          21,318,381   269,827,739   248,509,359  83 Linux
/dev/sda8         269,827,803   280,446,704    10,618,902  82 Linux swap / Solaris
/dev/sda4          16,787,925    21,318,254     4,530,330  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        002CA9622CA95386                       ntfs       RECOVERY                      
/dev/sda2        A48E552B8E54F6F0                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        0caaedfe-da0e-459e-9610-1bc52e4e44f4   ext4                                     
/dev/sda5        bd98abbd-d535-488a-aee4-6bb887114cc8   ext4                                     
/dev/sda6        1c2863c7-8f55-47cb-be45-d04c248304de   swap                                     
/dev/sda7        fef3edcd-d596-4fc8-8c81-39ae035d979e   ext4                                     
/dev/sda8        48db29d9-6146-4274-9b78-989f1da1249e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
```

---

### Post by tnngator on 2011-01-22
kid might download and try 
**Super Grub Disk**

will boot anything that can be ,,has worked for me in times of need LOL

---

### Post by Rubi1200 on 2011-01-22
Thanks for the results wcutrombonekid.

You do not appear to have posted the entire contents of the file or was this everything?

There seem to be file-system errors on the Ubuntu install (probably a result of the situation you described).

This is what I suggest:

Boot the LiveCD again and run the following commands;

```
sudo e2fsck -C0 -p -f -v /dev/sda7
```If this reports errors (likely) then run this;

```
sudo e2fsck -f -y -v /dev/sda7
```Reboot and let me know what happens.

---

### Post by wcutrombonekid on 2011-01-22
FIXED!

thank you so much! everything is just as I left it!

you have no idea how many of my files you saved!

---

### Post by Quackers on 2011-01-22
Nice one Rubi1200 :-)

---

### Post by Rubi1200 on 2011-01-23
No problem, you are more than welcome wcutrombonekid :)

Please mark this thread Solved using the Thread Tools near the top of the page.

@Quackers; thanks mate :)

---

### Post by wcutrombonekid on 2011-01-23
i'm not very good with the command line.  I see you "fsck'd" it or whatever, and I know what that means.  It seems like there was very little difference between the two lines of code you gave me.  What was the difference in the two in telling the computer what to do?

---

