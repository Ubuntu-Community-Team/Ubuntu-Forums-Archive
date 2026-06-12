---
title: "help"
date: 2011-05-20
forum: General Help
---

### Post by ezcuincle on 2011-05-20
Hello, 
I updated ubuntu to the newest version few days ago, but it only worked for couple days.  Now, I just get something like this when I turn it on:

--------------------------------------------------------

try (hd,00) NTFS5:  error prefix not set

GNN GRUB version 1.99~rc1-13ubuntu3
Minimal BASH-LIKE line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB list possible device or file completions.
GRUB>

---------------------------------------------------------

Ive been reading some of the forums but im pretty lost, Iam new with linux.  I have som important files there that I would like not to get lost.  The computer is partitioned in windows xp and linux.  

thank you very much.

---

### Post by Rubi1200 on 2011-05-20
Hi and welcome to the forums :)

Please do the following so we can get a better overview of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script for 11.04 at the end of this post.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

new script for 11.04
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

---

### Post by ezcuincle on 2011-05-20
thanks,  can you send me link for LiveCD?

---

### Post by doron387 on 2011-05-20
download ubuntu  from :

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

i recommend to install it to a usb flash stick using the very simple installer, downloaded from here :
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

it gone a be faster than using live cd

and then, when you start your pc, press F2 or ESC or whatever you need to get to the bios screen in order to choose the usb as first boot option.

if you don't understand a word from what i have just written, stick to burning the downloaded image using NERO or other software .
burn it as an image.

happy to help
p.s. next time try to write in the title of the message something that people will know what is your problem in few words.
good luck

---

### Post by ezcuincle on 2011-05-20
damn! took me a while to download and set up the flash drive, but then when I reboot, and open the menu it doesnt give me the option to boot from the usb,  only gives me floppy drive-hard drive-cdroom and network.  what should I do now?

---

### Post by Rubi1200 on 2011-05-20
You need to burn the image to a CD and then select cdrom in BIOS when you boot the computer.

Two things to do before you start:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by linuxinstalledfromhdd on 2011-05-20
Downgrade to 10.10..  Use a step-by-step walkthough..  Don't mess with it too much for a few days and find out if you have a hardware issue.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by ezcuincle on 2011-05-21
ok finally go it, here is the info,  my big question is would I be able to recover the files I have in ubutu if install an older version as suggested in the forum?  this is what i care the most right now recover those files.   

thank you all for your great help.        


 ```
       Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
205 heads, 13 sectors/track, 43981 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   117,207,039   117,204,992   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B26442F46442BB3D                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

```

---

### Post by Rubi1200 on 2011-05-22
Are you able to boot Windows normally?

You have a Wubi install. However, the root.disk is missing. Do you know what happened?

Any data you had is on the root.disk and you need to try and find it to recover the data.

Boot into Windows and enable the option to view hidden files and folders.

Then, look for a file called C:\found.000 (or something similar). If you find the root.disk there, simply move it back to the Ubuntu folder at the root of the C drive.

Let us know if this helps.

---

### Post by ezcuincle on 2011-05-22
i dont know about the root.disk, i havent touch anything besides upgrading ubuntu.   I could not find the file on windows.  I tried couple options to recover files from LiveCD, and couldnt get to work anything. Still ubuntu not working and still files lost,  would there be a way to recover the files or should I just forget about it? 
i know i should had backup.

thanks

---

### Post by Rubi1200 on 2011-05-22
The problem is this; sometimes Windows or an antivirus software incorrectly identifies the root.disk as being a problem.

An AV program might quarantine it, Windows will move it to the hidden folder I mentioned before.

I would look again ncluding using the option for an advanced search from the Start menu.

Another thing to try (though I am not sure how well it would work) is to use a Windows software to look for and try and recover the root.disk.

Here is one option:
[http://www.piriform.com/recuva](http://www.piriform.com/recuva)

However, if you don't find the root.disk then the bad news is that you have lost whatever was saved on it.

---

### Post by ezcuincle on 2011-05-22
thank you very much again for the help.

---

### Post by ezcuincle on 2011-05-22
found it!  and placed it on ubuntu folder looks like this:
install
winboot
root.disk
ubuntu.ico
uninstall-wubi.exe

what should I do now?

---

### Post by bcbc on 2011-05-22
First - backup the root.disk, just in case.

Then the correct place is in the "disks" folder:
\ubuntu\disks\root.disk
and
\ubuntu\disks\swap.disk 

Then try to boot into Ubuntu and report back. If you can figure out what happened prior to it going missing - and where you found it, it might help others. One important thing is to avoid hard shutdowns (even if it appears to be hanging you should first try Alt+SysRq R-E-I-S-U-B before resorting to a hard shutdown).

---

### Post by Rubi1200 on 2011-05-23
> **ezcuincle said:**
> found it!  and placed it on ubuntu folder looks like this:
install
winboot
root.disk
ubuntu.ico
uninstall-wubi.exe

what should I do now?

This is great news. As bcbc mentioned, let us know how it goes booting back in again and where you found the file. This may help us help others in a similar situation in the future.

---

### Post by ezcuincle on 2011-05-23
Question?  Do i have to create the "disks" folder?  When I get into the ubuntu folder there is not a disks folder. 

Im not sure where I found it but I used the advance search and checked all the options except "case sensitive".  
Also now when I did a search again looking for the "disk" folder, what I saw is the "swap.disk" that you also mention, I don't know if the other one was there too.  And that "swap.disk" is in:
local disk (C:)
  folder: found.000
    folder: dir0000.chk
             boot(folder)  and  swap.disk

---

### Post by Rubi1200 on 2011-05-23
Yes, create the folders with the structure bcbc mentioned previously.

Also move the swap.disk to its folder.

Based on what you told us it seems likely Windows ran a chkdsk and moved the files to where you found them.

As bcbc mentioned, make a backup of the root.disk to an external medium such as a USB stick just in case this happens again.

---

### Post by ezcuincle on 2011-05-23
awesome!  it worked, a couple times just went back to a black screen instead of ubuntu, but by the third time it went through. 
However, it seems to be really slow, and also the way the graphics changed, I remember that happen also before it broke.  After update graphics looked certain way and two days after the graphics changed,  then it broke. So far I backed up all my data and Ill try a few days see how it goes.  

Thanks much for all your help.  This was fun.

---

### Post by Rubi1200 on 2011-05-24
Excellent! I am really pleased you got this sorted out. As long as you have a backup of the root.disk you should be covered for most situations.

Please mark this Solved using the Thread Tools near the top of the page.

---

