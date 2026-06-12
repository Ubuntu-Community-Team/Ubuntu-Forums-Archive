---
title: "Messed up GRUB loader. any fixes?"
date: 2010-10-27
forum: General Help
---

### Post by sodathepop on 2010-10-27
hey, i had a few partitions on a 250gb hd
had windows 7, vista and ubuntu 10.04

i had a grub for all these.

then i plugged in aother 40gb hadrive
and installed another ubuntu there to operate on another computer.

well now my computer HAS to have that harddive to boot any grub menu at all.
i was wondering where on my original 250gb is the boot grub located?

or how to delete this grub.

thanks for the help

---

### Post by ashton324 on 2010-10-27
Boot into one of the windows systems and download a piece of software called EasyBCD. That should help you repair the MBR and hopefully make it all bootable again.

---

### Post by sodathepop on 2010-10-27
thatnk you for the help. 
i will try that right now

---

### Post by ashton324 on 2010-10-27
ok write back with feedback when you have done it. EasyBCD repairs the windows MBR i dont know about GRUB but there should be some option in there. Ive had the same problem before and solved it with EasyBCD.

---

### Post by garvinrick4 on 2010-10-27
If you do not get up and going put a Ubuntu install cd in and choose try ubuntu and then open a terminal and run this.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
Download it to your DESKTOP and then run this in terminal
 ```
sudo bash ~/Desktop/boot_info_script*.sh 
```
It will put a text file on your desktop copy and paste it to this thread.
Will give the answer for correct instructions on how to put grub2 in MBR so
all OS's are bootable from grub menu.

---

### Post by oldfred on 2010-10-27
+1 on garvinrick4 suggestion of running the boot info script.


The script will tell us where everything is at. Typically grub installs to the MBR of sda, so your install of grub may have gone into the wrong drive. It is relatively easy to reinstall grub, but we need the details.

---

### Post by sodathepop on 2010-10-28
man i done messed up.

i tried but then woulnt load anything.
had to reinstall ubuntu on the 40gb
and the windows boot loaders are gone.
its asking to put recovery cd in.

haha i swear these grub menus pose the most annoying threat.
because windows 7's nt loader is different than xp

---

### Post by sodathepop on 2010-10-28
it says no such directory found..? on garvins idea..

---

### Post by Quackers on 2010-10-28
Did you download the file to your desktop?

---

### Post by sodathepop on 2010-10-28
okay this is what i got..


              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=ce0623c1-c1a8-48ae-9221-674e97942d08)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

---

### Post by oldfred on 2010-10-28
You did not post the entire script so I cannot verify that the UUID is correct, locations of boot flag for windows, and which Ubuntu grub2 is trying to boot.

Please post the entire results.txt inside code (#) tags. You highlight the entire results.txt  after you have pasted it in your message and in the edit panel above on  the right is a # or code tag auto inserter. You can hover over the icons  in the edit menu for explanation. You have to manually insert code tags  in your previous post. If I try to show the tags they get converted to  code tags and disappear. 

But it is like [ code] insert data here [ /code] without space in the bracket, this becomes:
     ```
 insert data here 
```You do have a grub4dos folder in you windows install in sta1. You should delete that.
/grldr

You also have a second windows install in sda5. Since that is a logical partition windows has moved its boot files to sda1 and sda5 will only boot thru sda1. Generally it is better to install windows to primary partitions.

How windows works:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

