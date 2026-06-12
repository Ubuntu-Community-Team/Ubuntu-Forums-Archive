---
title: "Ubuntu not booting correctly"
date: 2011-06-07
forum: General Help
---

### Post by acboyz2 on 2011-06-07
Hello,

I have been using Ubuntu for about a month now. I have the latest version, 11.04. Today, I was watching and downloading movies on Miro and while I was watching, the screen froze and I couldn't get it back to normal. I manually shut down the computer and when I turned it back on it brought me to a page that reads: 
"GNU GRUB version 1.99~rc1-13ubuntu3" 
and underneath it has 5 options: 
"Ubuntu, with Linux 2.6.38-8-generic"
"Ubuntu, with Linux 2.6.38-8-generic(Recovery mode)"
"Previos Linux versions"
"Memory Test (memtest86+)"
"Memory Test (memtest86+, serial console 115200"

when I choose the first option, it brings me to a screen that says: 
BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built in shell (ash) 
Enter 'help' for a list of built in commands.
(initramfs)

I do not know what to do from here or what the problem is, I was thinking maybe one of the movies I downloaded caused the problem because it happened right when I was downloading. Any help is appreciated, I really want to have my computer working again.

Thanks!

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

I think it is more likely that the file-system was damaged as a result of the hard shutdown.

In any event, please do the following so we can help you fix this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by acboyz2 on 2011-06-08
Thank you so much for your help! 

Here's the results.txt:

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   114,139,135   114,137,088  83 Linux
/dev/sda2         114,141,182   117,209,087     3,067,906   5 Extended
/dev/sda5         114,141,184   117,209,087     3,067,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        246b44ed-3f10-48bb-9c5e-406912fd2612   ext4       
/dev/sda5        77443575-b49d-45a1-a04c-ebfba075f4e4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Rubi1200 on 2011-06-08
Thanks for the results.

There does appear to be damage to the file-system:
> Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1

From a LiveCD run this command:

```
sudo e2fsck -f -y -v /dev/sda1
```

Once the command completes, and assuming no errors, reboot taking out the CD and you should be back in Ubuntu.

---

### Post by acboyz2 on 2011-06-08
It worked!! Thank you so much! You're a life-saver! Do you think that the torrents I downloaded had a virus or something? Should I delete them or are they okay?

---

### Post by Rubi1200 on 2011-06-08
Excellent! I am really pleased this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

It would be speculating to say the torrents were to blame and I doubt that was the case.

As I said, hard (manual) shutdowns can often cause problems like this.

In future, try and use this method to do a soft reboot:
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **acboyz2 said:**
> It worked!! Thank you so much! You're a life-saver! Do you think that the torrents I downloaded had a virus or something? Should I delete them or are they okay?

If I was using bittorrent I would definately want to scan everything I download with a antivirus program. You can install an antivirus program for Ubuntu if you are worried.  Here is a nice guide to 11.04 and how you can get that program installed on your system:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

It's listed about 1/3 the way down the list. :)

---

