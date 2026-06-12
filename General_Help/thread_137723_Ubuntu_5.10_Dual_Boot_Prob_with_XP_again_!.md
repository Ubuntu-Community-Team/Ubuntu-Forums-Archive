---
title: "Ubuntu 5.10 Dual Boot Prob with XP again !"
date: 2006-02-28
forum: General Help
---

### Post by Coulrophobe on 2006-02-28
This is all new territory for me having only just completed following [these]("http://users.bigpond.net.au/hermanzone/p3.htm") instructions to get my machine dual booted (Win XP Pro and Ubuntu)

Install of Ubuntu = flawless \\:D/ 
Log out and into Windows...pfft..unknown filesystem type, Grub error 0x7

_sudo fdisk -l_
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/hdb2            3732        4982    10048657+   5  Extended
/dev/hdb3            3041        3731     5550457+  83  Linux
/dev/hdb5            3767        4982     9767520    b  W95 FAT32
/dev/hdb6            3732        3765      273042   82  Linux swap / Solaris

_cat /boot/grub/menu.lst_
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
savedefault
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

I installed Grub to the MBR as per the instructions...soooo...this may well be the issue. Can someone point me toward a solution please ?

Many TIA
S

---

### Post by dcstar on 2006-02-28
[QUOTE=Coulrophobe]This is all new territory for me having only just completed following [these]("http://users.bigpond.net.au/hermanzone/p3.htm") instructions to get my machine dual booted (Win XP Pro and Ubuntu)

Install of Ubuntu = flawless \\:D/ 
Log out and into Windows...pfft..unknown filesystem type, Grub error 0x7
......
_cat /boot/grub/menu.lst_
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
**chainloader     +1**
......[/QUOTE]
Edit that file and try making the highlighted line:

chainloader     (hd0,0)+1

---

### Post by Coulrophobe on 2006-02-28
[QUOTE=dcstar]Edit that file and try making the highlighted line:

chainloader     (hd0,0)+1[/QUOTE]

Thanks DCstar but no joy...still getting the same filesystem type unknown :-k 
I just tried the unhide(hd0,0) directive in there too to no avail.
S

---

### Post by Coulrophobe on 2006-03-01
OK...so amending the menu.lst hasn't worked and from what I can see on the posts relating to this subject I have c0cked-up by installing GRUB into the MBR.

I can see there's a lot of suggestions to use the WinXP recovery console to get the WinXP partition back to life but what is this going to do to my Ubuntu install ? How do I make sure that that will still boot ? Should I start again but install GRUB somewhere else ?

Any advice greatly appreciated.
TIA
S

---

### Post by gwilson on 2006-03-01
Here's some general advice from a guy who is not so much a newbie.  ;-)

Read the entire message before proceeding.

I have my drives divided into numerous partitions and install various operating systems to run on the same machine. I have managed to mess up an otherwise working system several times, and I have one good suggestion for you. Some time back, someone wrote in to say that you could solve a lot of problems by going through a sort of "mock" install of Ubuntu 5.1 in which you go through the partitioning step, install grub and abort the installation. I have done this numerous times and it has never done any damage and has usually solved any problems I had. I believe it updates your fstab file in the process.

First of all, be aware that XP has a funny organizational structure wherein it actually boots from a small FAT32 partition into the NTFS partition. Why? Who knows? I notice that all the info you sent refers to /dev/hdb. Presumably, you have a /dev/hda also, and that may be where XP needs to boot from. Which hard disk is your CMOS setup configured to boot from? HD0 that is /dev/hda or HD1 that is /dev/hdb? If you changed which drive has boot priority that could be affecting you.  If you used to boot from HD0 /hda before you installed Ubuntu, you probably want to boot from that drive. That's all just stuff to keep in mind. 

Here's the partial installation procedure. Set up your system to boot from the CDROM, put the Ubuntu 5.1 installation CD in there and reboot. I may not remember every screen, but this will guide you through it. Hit return as you would to start a normal installation. Ubuntu will ask you what keyboard and language you have; in the USA you can just hit return for the defaults. Ubuntu will load a bunch of files into working memory without installing them to your hard drive. Then it will detect what hardware you have and begin to set up your network; if it doesn't find your network, that's no problem at the moment (when I had a slower network card, I used to have to have it search for the network several times before it found it; now it does it first shot). You can skip this step if you want to. 

Bear with me, I'm getting there. After it finished with your network, it will start the partitioning program. You can mess things up here, but if you are just a little careful, it's no problem. After the partitioner starts, Ubuntu will present you with various options. At the bottom, you can choose to edit the partition table manually. Select this option. Next, you will see all of the partitions on your system. Various partitions will have suggested mounting points under /media. You must find your main Ubuntu partition which I think in your case is hdb3. Go down and highlight that partition and select it. Change the mounting point from /media/hdb3 (or whatever it is) to / . If you select the mounting point line, it will let you select / as the mounting point. Then go down and tell it you are finished making changes to this partition. You return to the previous screen and tell it you are ready to write changes to the partition table. Confirm this as necessary, and it will write your new partition table. (I don't think there are any warning screens here, but if there are just hit continue.)

Now find your way back to the general list of installation steps. Skip down past all the stuff about installing packages and go to Install Boot Loader or Install Grub or whatever it says. Tell it to install Grub to the MBR. You will probably see a couple of warning screens. Don't worry. Hit continue. The default will install it to the MBR of the drive that has first boot priority in your CMOS setup. Go ahead and let it do so. Windows XP may mess up you MBR for Linux, but I have never had Grub mess up the MBR for XP. It's a very smart and efficient program.

After Grub has installed, go back to the table of installation and skip down to Abort Installation and select it. Continue through any warning screens, and reboot your system.

I have done this a hundred times. It actually takes about five minutes, and it has never created any problems while solving many. The Ubuntu 5.10 Grub installation program is very well written. It doesn't have a beautiful graphic interface, but it always seems to detect all of the partitions on my system correctly including various versions of Windows and some obscure versions of Linux. I have even used this preocedure to correct problems caused by the fancy Grub installation program in Suse. As long as you don't specifically tell it to delete a partition or tell it to install packages, it will not overwrite any data already on you computer. It works great.

One last hint. I installed Suse the other day, and Windows XP would no longer boot properly. I let the system sit with a black screen for a while and it eventually cleared itself. It must have been doing some sort of diagnostic routine. Then I did the procedure outlined above. It found all of the partitions and operating systems on my computer flawlessly, overwrote the fancy Suse bootloader, and sorted everything out just fine.

Try it.

Glen

---

### Post by hugo491 on 2006-03-01
I STRONGLY SUGGEST THAT YOU TRY THIS METHOD BEFORE YOU DO ANYTHING THAT MAY DAMAGE YOUR WINDOWS OR LINUX PARTITIONS!!!!
alright, well this may be a long shot but we need to experiment a bit. As a side note, I had a similar problem before and this helped. First, restore the menu.lst to the way it was before you started to change it. (the windows one) 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

After that try booting windows (just in case) If it does not work... we will go through a sequence where you modify a line. Doing so may bring up windows, but ONLY modify the one for windows. First try:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

Then:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

Then:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,1
savedefault
makeactive
chainloader +1

(so on and so forth, do so until you get to 3,3) ALSO: remember skip 0,2 since that's linux), hopefully that long and slightly tedious fix will give you back windows.

---

### Post by hristo.doynov on 2006-03-01
Hi there.

I am a complete newby, so do not expect miracles ot of my post, but I have experienced exactly the same scenario - flawless Ubuntu install and GRUB Error 7 because of my ignorance - I had my Ubuntu installation partition disk striped with another under WinXP Pro. Actualy the MS OS warned me that I will be unable to boot other OS, but I ignored it completely.

Hope this helps in any way :)

[QUOTE=Coulrophobe]This is all new territory for me having only just completed following [these]("http://users.bigpond.net.au/hermanzone/p3.htm") instructions to get my machine dual booted (Win XP Pro and Ubuntu)

Install of Ubuntu = flawless \\:D/ 
Log out and into Windows...pfft..unknown filesystem type, Grub error 0x7

_sudo fdisk -l_
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/hdb2            3732        4982    10048657+   5  Extended
/dev/hdb3            3041        3731     5550457+  83  Linux
/dev/hdb5            3767        4982     9767520    b  W95 FAT32
/dev/hdb6            3732        3765      273042   82  Linux swap / Solaris

_cat /boot/grub/menu.lst_
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
savedefault
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

I installed Grub to the MBR as per the instructions...soooo...this may well be the issue. Can someone point me toward a solution please ?

Many TIA
S[/QUOTE]

---

### Post by Coulrophobe on 2006-03-01
> **gwilson]Here's some general advice from a guy who is not so much a newbie.   said:**
> Interestingly no...I only have hdb...single disk in this machine. Wonder why it's being recognised as hdb and not hda ? [/COLOR]

<SNIP!>
Glen

Wow...a detailed and highly succinct explanation Glen. Fantastic mate...exactly what I was looking for. I'm going to try Hugo's trial-and-error method detailed below your post first (one of the first things I did was a 'hit and hope' change to the menu.lst to set root (hd0,1) but to no avail !) then I will get into the process of your update as you suggest.

Will report back either way with results this evening. Thanks all for your input.

Best regards
Scott

---

### Post by brucetan on 2006-03-01
hi Glen,
I am trying to install ubuntu to my external usb IDE HD and keeping my window XP on the internal IDE drive.  The notebook is a DELL Inspiron 6000.

When the ubuntu installation came to the part of writing grub loader to MBR.  I said no and selected my ext USB HD (/dev/sda) instead.

before testing the Ubuntu after installation, I wanted to test if my Window XP is still working.  I disconnected the USB drive to see if Window XP would boot up.  It gave me a shock that it shown me:

GRUB Loading stage1.5.
GRUB loading, please wait...
Error 21

And the system just stopped there....

I then try to connect the USB drive and rebooted it.

It showed me a list of OS to select, the last of the list is my WindowXP. I did that and it works.

However, if I select ubuntu from the list then it ran for a while then gave me panic..  This seems to me that the installation did not go well and also somehow writing a GRUB bootloader to my internal HD.

Can you if there is anywhere to get rid of the GRUB bootloader from my internal HD and still not damage to my WindowXP & data?

Best regards,

Bruce

---

### Post by Ramses de Norre on 2006-03-01
> Interestingly no...I only have hdb...single disk in this machine. Wonder why it's being recognised as hdb and not hda ?

The hda and hdb tags are related to your IDE controllers, hda is the master of the first IDE controller, hdb the slave. Idem dito for the second IDE controller and hdc and hdd.

So I guess you harddrive is at the slave connector of your first IDE controller.
That's ok though I guess.

---

### Post by Coulrophobe on 2006-03-01
[QUOTE=Ramses de Norre]The hda and hdb tags are related to your IDE controllers, hda is the master of the first IDE controller, hdb the slave. Idem dito for the second IDE controller and hdc and hdd.
So I guess you harddrive is at the slave connector of your first IDE controller.
That's ok though I guess.[/QUOTE]

Aaaahhh...! I see. Thanks for that Ramses
S

---

### Post by gwilson on 2006-03-01
Bruce wrote:

hi Glen,
I am trying to install ubuntu to my external usb IDE HD and keeping my window XP on the internal IDE drive. The notebook is a DELL Inspiron 6000.

When the ubuntu installation came to the part of writing grub loader to MBR. I said no and selected my ext USB HD (/dev/sda) instead.

(snip)

Can you if there is anywhere to get rid of the GRUB bootloader from my internal HD and still not damage to my WindowXP & data?

Best regards,

Bruce

Well, you're throwing me a bit of a curve, Bruce, because you wrote to the USB drive instead of the internal drive. First of all, don't panic. You can get your Windows XP system back. On my desktop system, I use GRUB as the bootloader for everything, including Windows XP. When my system boots to the first internal hard drive MBR, I get the list of operating systems. One of them is Windows XP. I highlight that and hit return. On my system, the next screen I see gives me a choice of booting Windows XP or Windows 98/ME. Depending on how XP was installed on your system, you may not see this screen, that is, it would go directly into XP. (I had ME on my system when I installed XP.)

To get back to your original state, you would have to do some Windows XP funny stuff. In Windows 98 and ME, this was very simple, but XP reportedly has a very non-user-friendly boot process. I don't know if you can get things back with your installation disk and some sort of restore or repair function in XP. However, you can get XP back using GRUB.

My recommendation is that you do the following. Think before you do anything and consult others if you want to. Attach your USB drive again and boot to the Ubuntu CD. Go through the same steps you did before. Designate the Ubuntu installation on the USB drive as / again when it comes up in the partitioning procedure. Go through the routine described previously and do the GRUB installation. This time, write GRUB to the MBR of the internal drive, as the default suggests. Abort the installation as before.

I believe this will give you the selection of operating systems when you boot up the laptop and allow you to select Windows XP regardless of whether or not the USB drive is present. Obviously, if the USB drive is absent, you'll have problems booting Ubuntu.

If you do this, GRUB will be the bootloader on your internal hard drive. For me, this is fine and works like a charm. If you want to get rid of all traces of Linux and GRUB from your system, you'll have to work some Windows magic with the MBR on the internal hard drive that I can't help you with. However, there's no reason why you can't just use GRUB forever.

I hope you're satisfied with this. When I made my remarks, I was really speaking only to the circumstances the original questioner had. You had different hardware and deviated from the procedure I described. What I've described this time round will allow you to boot into XP without the external drive connected, but you do have to go through GRUB (which is, after all, an excellent boot loader).

Good luck.

Glen

---

### Post by Coulrophobe on 2006-03-01
[QUOTE=gwilson]Here's some general advice from a guy who is not so much a newbie.  ;-)

Bear with me, I'm getting there. After it finished with your network, it will start the partitioning program. You can mess things up here, but if you are just a little careful, it's no problem. After the partitioner starts, Ubuntu will present you with various options. At the bottom, you can choose to edit the partition table manually. Select this option. Next, you will see all of the partitions on your system. Various partitions will have suggested mounting points under /media. You must find your main Ubuntu partition which I think in your case is hdb3. Go down and highlight that partition and select it. Change the mounting point from /media/hdb3 (or whatever it is) to / . If you select the mounting point line, it will let you select / as the mounting point. Then go down and tell it you are finished making changes to this partition. You return to the previous screen and tell it you are ready to write changes to the partition table. Confirm this as necessary, and it will write your new partition table. (I don't think there are any warning screens here, but if there are just hit continue.)

Glen[/QUOTE]

Glen,

Followed the instructions and Ububtu still boots no problem but still getting the continuing Grub error for Win XP on (hd0,0) :-k 

Any further advice for me to try out ?
Best regards
S

fdisk -l & cat output follows:
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/hdb2            3732        4982    10048657+   5  Extended
/dev/hdb3            3041        3731     5550457+  83  Linux
/dev/hdb5            3767        4982     9767520    b  W95 FAT32
/dev/hdb6            3732        3765      273042   82  Linux swap / Solaris

------------------------------------
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by gwilson on 2006-03-01
We may be getting out of my league here, now. My menu entry for my XP partition looks like this. I'm not sure what the "map" entries are. I didn't put them in there manually as far as I can remember. I have two internal drives.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I wonder what your /etc/fstab file looks like? Mine is plain vanilla, like this:

/dev/hdb5       /media/hdb5     ntfs    defaults        0       0

Glen

---

### Post by Coulrophobe on 2006-03-01
[QUOTE=gwilson]We may be getting out of my league here, now. My menu entry for my XP partition looks like this. I'm not sure what the "map" entries are. I didn't put them in there manually as far as I can remember. I have two internal drives.

I wonder what your /etc/fstab file looks like? Mine is plain vanilla, like this:

/dev/hdb5       /media/hdb5     ntfs    defaults        0       0

Glen[/QUOTE]

Sadly this is all moot now Glen - necessity means I have to get back to my Win partition so in goes the old WinXP setup disk and a repair is underway as I type.

Many thanks for your time and efforts in trying to help resolve my problems. Next time I'll probably be on trying to gt Ubuntu back onto my old SV24?! \\:D/ 

Thanks again and best regards
Scott

---

### Post by brucetan on 2006-03-02
Many thanks Glen!

I managed to normalize my internal HD partially  through:
(1) booting from Original Window XP home set up CD;
(2) Enter into repair mode ==> "R"
(3) Run FixMbr
(4) then run Fixboot

This got rid of the Grub loader error and goes straight into the normal XP booting screen during boot.
However, I notice the dell's diagnostic partition (50MB) is now not usable.  I will have to contact Dell technical support to help recover it.

I probably would try the ubuntu installation on my notebook for a while until I ve done more research on the installation requirements.

Thanks anywhere.  Hope the above helps the others who face the same problem.

---

### Post by brucetan on 2006-03-02
Does anyone know where I get a documentation on ubuntu's 'naming' structure for hard disks whether it is internal IDE/SCSI/SATA or external USB disk? i.e., why /dev/hda or /dev/sda, etc.

---

### Post by brucetan on 2006-03-03
found out you can ran Live CD and under [System]-->[Administrator]-->[Disks], it would show your hard disk devices and the correct /dev reference path.  

Alternatively, on the command prompt, you can enter the following:
sudo fdisk -l

---

### Post by brucetan on 2006-03-03
by the way, I have successfully installed ubuntu onto my external USB drive while keeping my XP on internal HD of my DELL Inspiron 6000 notebook untouched.  I followed the process from Dave, see [http://www.ubuntuforums.org/showthread.php?t=80811]("http://www.ubuntuforums.org/showthread.php?t=80811")

Hope you all benefit from his guide.

---

### Post by akiro.yamamoto on 2006-03-03
[QUOTE=Coulrophobe]T

Install of Ubuntu = flawless \\:D/ 
Log out and into Windows...pfft..unknown filesystem type, Grub error 0x7

_sudo fdisk -l_
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/hdb2            3732        4982    10048657+   5  Extended
/dev/hdb3            3041        3731     5550457+  83  Linux
/dev/hdb5            3767        4982     9767520    b  W95 FAT32
/dev/hdb6            3732        3765      273042   82  Linux swap / Solaris

_cat /boot/grub/menu.lst_
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
**makeactive**
chainloader     +1

<CROP>

I installed Grub to the MBR as per the instructions...soooo...this may well be the issue. Can someone point me toward a solution please ?

Many TIA
S[/QUOTE]
Please remove
makeactive
I had the same problem and no matter what everyone else said, that did the trick.
That partition is already active, grub tries to activate that partition and fails ;)

---

### Post by Coulrophobe on 2006-03-03
[QUOTE=akiro.yamamoto]Please remove makeactive I had the same problem and no matter what everyone else said, that did the trick. That partition is already active, grub tries to activate that partition and fails ;)[/QUOTE]

Many thanks Akiro but I never managed to boot both OS so had to revert to XPPro...rescue -> Fixmbr -> fixboot also failed leaving me with an unbootable heap so FDisk it all was the only option.

XP back on and machine ghosted back to former core build...now where did I put that BF2 install & patch disk....

PS..Ubuntu now happily installed on my old Shuttle SV24 Via Samuel 733, 256Mb ram, 6gb disk. Some if the installs failed to complete but she's bootable and once logged in and my broadband connection comes back up [another story ! :mrgreen: ] I'll apt-get update and clean it all up and I reckon I'll be just dandy. Then let the tinkering begin ?!?!?

Cheers to all that pitched in...
S

---

