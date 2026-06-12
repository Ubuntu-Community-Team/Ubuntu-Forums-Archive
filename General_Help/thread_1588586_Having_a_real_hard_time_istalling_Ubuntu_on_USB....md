---
title: "Having a real hard time istalling Ubuntu on USB..."
date: 2010-10-05
forum: General Help
---

### Post by chooyanzou on 2010-10-05
To make the partitions needed to install Ubuntu on my USB stick and still be able to save and install on it, even though it is run as Live CD, I aparently must make the partitions while inside Ubuntu. To do that I have tried several times to download the wubi.exe for windows istallation but everytime I try to run the wubi.exe file I get this message:

[pyrun.exe] There is no disc in that unit. Insert a disc in unit \Device\Harddisk1\DR1.

What can be the problem?

---

### Post by sanderd17 on 2010-10-05
Your question is not quite clear. What do you want?

* put a live image on an USB stick, so you can run ubuntu when the USB stick is plugged in and you can store (a little) data and settings on it. This is good if you want to test ubuntu for a few hours/days.

* install ubuntu inside windows with wubi. This is good if you want to test ubuntu for a few weeks.
PRO: 
    + ubuntu is always availiable on your computer
    + don't need repartitioning so it's easy to remove ubuntu.
CON:
    - if windows breaks, ubuntu is broken too
    - ubuntu works slower than a normal install and is more vunerable for crashes

* install ubuntu on a separate partition. This is the only "permanent" install.
PRO:
    + works fast and stable
    + less risk for data loss once ubuntu is installed
CON:
    - not portable
    - not easy to remove ubuntu.

---

### Post by chooyanzou on 2010-10-05
What I want to do is to divide my USB memory stick into two partitions and run Ubuntu 10.04.1 as a Live CD from one partition and save my settings and installed applications on the other partition. As of now I have managed to divide the actual memory stick and istalled Ubuntu 10.04.1 Live on the boot partition but I have quite some trouble making it remember my settings. It loses parts of my settings it seems. I add swedish keyboard layot and remove the USA layout, I add a terminal link on the desktop and I make some changes in the graphical apearance. Than on reboot the USA keyboard layout is back, alongside the swedish layout, the terminal link on the desktop is still there but my graphical apearance settings are back at dafault. So I wonder if I have missed some part when I created partition number two...  =/

What I want in short is to boot from partition sdb1 on my memory stick and record changes and store installed programs on sdb2... I haven't used Linux before but I have to use it soon in some courses on the university witch kinda puts me in the sh_t.

I'm greatful for all help available.

Best regards.

[EDIT]
I just noticed something. Most of my settings ARE infact saved. For example the keyboard layout problem. I can switch between USA and Swedish keyboard layout in the toolbar at the top of the screen, but when I go in to the settings section there is only Swedish keyboard layout installed. It seem like my settings are loaded to late for the system to apply them, there fore it rund using the live CD defaults or something... I really need some heavy guru'ism here... ;)

---

### Post by oldfred on 2010-10-05
How large is your USB flash drive? If 8GB or more just do a full normal install as if it is a regular drive. You should do a few settings since it is a flash drive but that is all that is different from a standard drive. You can fit a full install in 4GB but have almost no room to work and have to regularly houseclean. 

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
[http://ubuntuforums.org/showthread.php?t=1539342](http://ubuntuforums.org/showthread.php?t=1539342)
[http://ubuntuforums.org/showthread.php?t=1556519](http://ubuntuforums.org/showthread.php?t=1556519)

---

### Post by C.S.Cameron on 2010-10-05
Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by chooyanzou on 2010-10-05
Thanks alot Cameron. The partitions worked better this time. But I still don't seem to be able to save my settings or installed programs. What ever I do or change while running Live CD, it is all back to default after next reboot.  =(

I'm running a 4GB Kingston USB stick (fast as hell really, gotta recommend it!)
I now have three partitions. sdb1(1GB, boot, FAT32), sdb2(1.5GB, ext3, casper-rw) and sdb3(1.5GB, ext3, home-rw).
I am running Ubuntu 10.04.1 on the boot partition.
It works perfectly except for the fact that nothing can be saved in either one of the extra partitions (casper-rw or home-rw)

Running out of ideas here...

---

### Post by jfed on 2010-10-05
I agree with sanderd17,You weren't all that clear. However I do know a quite easy way to install a linux based OS off of a USB.

Install UNetbootin.

```
sudo apt-get install unetbootin
```

It's really simple and easy to figure out on the spot. Although it has a feature that will download the OS directly through the program which usually gives me nothing but problems. So here is what I recomend doing.

Download the Ubuntu 10.04 iso (or whatever version you want .iso) Once you've done this open UNetbootin and browse to it, it should already have the USB selected, of course it has to be in for this to work.

Honestly I have no idea what you were talking about with partitioning. Were you saying you need to partition the actual USB drive? I dunno, but I do know, that this works.

---

### Post by chooyanzou on 2010-10-05
Yeah. I have partitioned my USB drive. It contains one boot drive (FAT32 formated) and one other partition named "casper-rw" that was meant to store saved documents and settings. In the boot partition I'm running Live CD. I do this to minimize the writing to the USB drive.

First partition:
FAT32 format
1 GB size
Boot
Live CD

Second partition:
ext3 format
1.5 GB size
caspar-rw

Third partition:
ext3 format
1.5 GB size
home-rw

What I'm trying to do, is to boot from the LiveCD version of Ubuntu wich I have "installed" on the boot partition. And when I shutdown or reboot I want my documents and settings to be saved on the other two partitions. I have heard something about "persistent", that will make it work. But to make the boot partition "persistent" I have to configure it as root. And of some reason it is not possible to login as root while running LiveCD... =(  It asks for the password all the time, wich I donät have, cause I didn't create the root account... =/

---

### Post by Zimmer on 2010-10-05
[http://www.pendrivelinux.com/usb-pendrivelinux-install-tutorial/](http://www.pendrivelinux.com/usb-pendrivelinux-install-tutorial/)

See if you can find what you want here...

---

### Post by chooyanzou on 2010-10-05
Now I'm getting even more confused...  When I list the file "text.cfg" in which I have to make changes to make the boot partition persistent I get the message that the file is read only.

-rwxr-xr-x 1 root root    706 2010-10-05 22:58 text.cfg

These flags should tell me that only ROOT has write access, right? But even if I'm editing the file as ROOT, I still get the same message "Read only file, only owner can change it"...  =(  Do I have to become mega-root or some supernatural god-like user to change it...?  I quickly approach the state of mental breakdown. :/

---

### Post by C.S.Cameron on 2010-10-05
Did you edit the txt.cfg file to add persistent?:

append noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --


You can also press F6 at the first boot screen and type " persistent" each time you boot.

---

### Post by chooyanzou on 2010-10-05
Thanks alot Cameron. Yeah I tried but I needed root access to write to text.cfg and even when I changed the text.cfg-file as root, it still denied me access. "Only the owner can change the file, etc, etc..." But I tried to halt the boot sequence and manually type "live persistent" at the prompt, and when finished booting I could change the text.cfg file AND save it. =) So now everything works like a charm! Well, except for one thing. That stupid first welcome screen on which one is prompted to choose whether to install Ubuntu on the hard drive or launch it as Live CD. As I intend to use it exclusively as Live CD it is beyond annoying to click it every time I boot. But hey, you can't have it all, right? ;)

So for now I guess it's on with the studies. Even though it's almost two in the middle of the freaking night here, I have about 10 hardcore Cisco networking assessments to finish! How awesome is that...? :P

And again, thanks a lot everybody, for all the help you've provided this lost newbie Ubuntier, especially you Cameron. Great step by step-list!

Best regards.
/Chooyanzou

---

### Post by C.S.Cameron on 2010-10-06
In 10.04 Live, you can go to System/Administration/Users and Groups and add a user with password.
You can also go to System/Administration/Login Screen Settings and add log in rules.
You are not the only one who would like to get rid of the first screen when running the disk image.

---

### Post by chooyanzou on 2010-10-12
The benefits running Live CD from a memory stick was not enough. The boot time with "persistent" mode became to long. Five and a half minute. Before putting it into persisten I had a boot time on about 30 seconds from the memory stick. Even though I have quite a fast stick. So I'm sorry to say, but I'm leaving the Live CD idea. I will probably need more of your expertise, Cameron, as I will try to fully install Ubuntu on the memory stick. So if you're sitting on some superhero-like tips n trix, those would be gratefully appreciated.

=)

/C

---

