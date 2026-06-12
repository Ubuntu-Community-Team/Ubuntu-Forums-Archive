---
title: "grub rescue&gt; no more Ubuntu nor XP"
date: 2011-05-09
forum: General Help
---

### Post by ideasbuenas on 2011-05-09
I've being using XP and 7 for a while. Now I decide to give a try to Ubuntu 11.04. I'd Run an install using gparted and now no Xp nor Ubuntu 11.04 booting and no Live CD can run (except for Slax). I think I did all wrong, coz now I only see grub rescue> at booting. Try to set and prefix or running LiveCD but nothing work. I've found a script with this results:                

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/hda and looks for b2d.

hda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

hda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

hda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

hdc: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e3b7e3b

Partition  Boot         Start           End          Size  Id System

/dev/hda1               2,046    20,514,815    20,512,770   5 Extended
/dev/hda5               2,048    18,534,399    18,532,352  83 Linux
/dev/hda6          18,536,448    20,514,815     1,978,368  83 Linux
/dev/hda2    *     20,515,005   160,071,659   139,556,655   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda2        AAD83924D838F065                       ntfs                                     
/dev/hdc                                                iso9660    SLAX                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/hda2        /mnt/hda2                fuseblk    (rw,noatime,allow_other,blksize=4096)


================================ hda2/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

==================== hdc: Location of files loaded by Grub: ====================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdd 
=============================== StdErr Messages: ===============================

File descriptor 11 left open
  No volume groups found
mdadm: No arrays found in config file
```

I did it from Slack. Please be patient.I need my XP back. And I still want to try Ubuntu 11.04, of course. Thanks

---

### Post by ideasbuenas on 2011-05-12
Again, something u don't undestand guys ????????

---

### Post by ideasbuenas on 2011-05-12
Maybe I'm doing something wrong? Could someone help ?

---

### Post by Rubi1200 on 2011-05-12
Hi and welcome to the forums :-)

Do you know what was on hda5 and hda6? There are errors mounting the file-system.

What exactly got you into this situation and what have you done since posting?

We need to understand what is going on before moving ahead.

Do you have backups of important data?

Which version of Slax are you using?

---

### Post by ideasbuenas on 2011-05-12
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Do you know what was on hda5 and hda6? There are errors mounting the file-system.

What exactly got you into this situation and what have you done since posting?

We need to understand what is going on before moving ahead.

Do you have backups of important data?

Which version of Slax are you using?
Well,tks for answering. In /hda5 and /hda6 I tried to install Ubuntu 11.04 on 10.04. I erased the 10.04 with gparted and then everyting gone wrong.

When I boot the computer the grub rescue> line shows itself, I tried to set and prefix but ls give me this: (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (fd0). I don't understand this.

From Knoppix 6 or Slax 3.5 I can run the script mentioned above. I can't run Ubuntu 11.04 LiveCD from my CD recorder. I don't know much about MBR o Grub2.  I dont have back up data and I don't wanna lose my folders. Since posting I use Slax 3.5 booting from CD.

---

### Post by wilee-nilee on 2011-05-12
> **ideasbuenas said:**
> Well,tks for answering. In /hda5 and /hda6 I tried to install Ubuntu 11.04 on 10.04. I erased the 10.04 with gparted and then everyting gone wrong.

When I boot the computer the grub rescue> line shows itself, I tried to set and prefix but ls give me this: (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (fd0). I don't understand this.

From Knoppix 6 or Slax 3.5 I can run the script mentioned above. I can't run Ubuntu 11.04 LiveCD from my CD recorder. I don't know much about MBR o Grub2.  I dont have back up data and I don't wanna lose my folders. Since posting I use Slax 3.5 booting from CD.

This XP
```
hda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```


Is the only thing resembling what would normally be seen and may be fixable.
If you have a XP disc boot it to the repair command line and run this command.
/fixmbr
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you don't have a XP cd you can load a linux bootloader called LILO with a live ubuntu cd, click the universe repo on in the software sources, do a update and run these commands.

Restore basic windows boot loader - **universe enabled**
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR loaded.

If this gets you into XP; back it up then ask for help getting set up, I see no windows 7, do you have more than 1 hard drive?

---

### Post by lukeroge on 2011-05-12
Oh no, its never a good idea to delete Ubuntu's partition. Doing that will usually break the bootloader, aka grub. Without a working grub you can't boot up your computer properly. To get the bootloader back open up a terminal on the livecd and type "grub-install". This might work to reinstall grub and get windows working again. I have never tried it so I'm not sure

---

### Post by wilee-nilee on 2011-05-12
> **lukeroge said:**
> Oh no, its never a good idea to delete Ubuntu's partition. Doing that will usually break the bootloader, aka grub. Without a working grub you can't boot up your computer properly. To get the bootloader back open up a terminal on the livecd and type "grub-install". This might work to reinstall grub and get windows working again. I have never tried it so I'm not sure

Look closely at the script it shows no valid usable install left but XP, the Linux is not there it was a bad load. Grub got to the mbr but there is no evidence that any of the rest did.

The OP wants to conserve the files in XP that is what we are doing here.

Run the script in my signature for your self and compare it to theirs you will see what I mean.;)

As well the command grub-install is incorrect.;)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by ideasbuenas on 2011-05-12
> **wilee-nilee said:**
> This XP
```
hda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```


Is the only thing resembling what would normally be seen and may be fixable.
If you have a XP disc boot it to the repair command line and run this command.
/fixmbr
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you don't have a XP cd you can load a linux bootloader called LILO with a live ubuntu cd, click the universe repo on in the software sources, do a update and run these commands.

Restore basic windows boot loader - **universe enabled**
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR loaded.

If this gets you into XP; back it up then ask for help getting set up, I see no windows 7, do you have more than 1 hard drive?
It works like a charm !! I'm back to XP and recover all my folders. Just use an old XP CD, fixmbr and fixboot. Think a need to learn a little bit more to install Ubuntu 11.04. But, I will do it. Thanks you all.Good job!!

---

### Post by Rubi1200 on 2011-05-13
Glad you got things sorted out and good work from wilee-nilee.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

