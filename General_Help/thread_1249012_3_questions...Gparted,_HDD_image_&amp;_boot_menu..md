---
title: "3 questions...Gparted, HDD image &amp; boot menu."
date: 2009-08-24
forum: General Help
---

### Post by johnnydotexe on 2009-08-24
1.  I am running Ubuntu 9.04 alongside of Win XP Pro on an 80GB HDD, on my laptop.  The Ubuntu Updater is teling me it needs xxx space to download and install the updates, so which Ubuntu partition needs to be increased?  How do I decrease the windows partition and increase whatever Ubuntu partition if all of them appear to be locked?

2.  When I boot up my computer, I want it to default to windows instead of Ubuntu if I don't pick an option myself within X amount of time, like it does now except vice-versa.  Can this be changed?

3. I plan on buying a new 320GB HDD for this laptop.  If I buy the laptop-HDD adapter to hook them up to my desktop, can I copy the contents of the 80GB over to the 320GB with something like Acronis True Image?  Or is there an easier way, or better software to accomplish this task?

---

### Post by Warren Watts on 2009-08-24
> **johnnydotexe said:**
> 2.  When I boot up my computer, I want it to default to windows instead of Ubuntu if I don't pick an option myself within X amount of time, like it does now except vice-versa.  Can this be changed?

I can help you with #2...  All you have to do is edit **/boot/grub/menu.lst** and move the lines that refer to booting the Windows partition at the top of the list of bootable partitions.

---

### Post by johnnydotexe on 2009-08-24
Thanks!  I'll give that a try once I'm done playing around on CoD4.

Still needing answers to #1 and #3. :)

---

### Post by louieb on 2009-08-24
1. depends on how your partitions are setup. To remove the lock Gparted has to be run from a Live CD.
2. The windows entry needs to be move way up further that the previous poster suggested. find the lines and put it between these lines. failure to do so will result in your windows entry disappearing next time there is a Kernel update. 
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

```

3. Guess Acronis True Image would work - have not used it. I use Gparted, others use Clonezilla both available on  the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")

Gparted can copy and resize at the same time. only disadvantage is it does not copy the boot code in the MBR. and that take about a minute to fix, not a problem.
[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by johnnydotexe on 2009-08-24
I found those lines that I need to put it between, but I'm not exactly sure what lines I need to move.

Here's what's at the end of my main.lst...

```
## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```As for my partitions, I thought they only set up one way by default when installing ubuntu.  I did a normal install from the liveCD, but chose to do the dual-boot option.  Now I can't install or download anything on Ubuntu, keep getting warned that I don't have enough space on the "/" partition...but all three start with a "/" from what I'm seeing in gparted.

In gparted they are listed as...

/dev/sda1   File System-ntfs   Size-72.03GiB   Flags-boot

/dev/sda2   File System-extended   Size-2.50GiB

/dev/sda5   File System-ext3   Mount Point-/   Size-2.33GiB   Used-2.09GiB   Unused-245.54MiB

/dev/sda6   File System-linux-swap   Size-172.54MiB

---

### Post by Warren Watts on 2009-08-24
> **louieb said:**
> 2. The windows entry needs to be move way up further that the previous poster suggested. find the lines and put it between these lines. failure to do so will result in your windows entry disappearing next time there is a Kernel update.

Oops!  You are absolutely correct.  I entirely forgot about that.  And you would think I would have remembered that, considering I have had that very thing happen to me.

---

### Post by AlexanderDGreat on 2009-08-25
Hey, so you did automatically setup partitions when installing ubuntu right? If you could go to system>administration>system monitor, go to the tab File Systems, you will see windows-like-report of your available space in your hard drive.

Also take note, how ubuntu automatically setup your partition, for me, I do it manually with 4 partitions: /boot (pri), / (log), /home (log), /swap (log)

Ubuntu normally names them sda1, sda2, sda5, notice the jump? It's because only 4 primary partitions are allowed in our hard disks, dunno why, so they're reserved to sda1234, sda5 is a logical partition that is.

For me, I usually just edit the default:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

Just count start from 0, whenever you see title Ubuntu, title Microsoft Windows XP, etc... the number is your default OS.

---

### Post by louieb on 2009-08-25
> **johnnydotexe said:**
> I'm not exactly sure what lines I need to move.
Move or copy these
```

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```> As for my partitions, ITypical setup - installer made the partition to small - goal make sda5 larger (look at the mount point column)  - make it at least 5GB - 10GB would be better. Even when I install on larger hard drives only make my / (root) partition around 10GB.

This must be done from a live CD. Just a recommendation - but I really like the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  another good one is the SystemRescueCD.
Make sure you defrag and run chkdisk 1st. 

create unallocated space by shrinking sda1 (your windows partition). press apply, when done reboot and make sure windows still works - it will probably want to run chkdisk on 1st reboot - let it and let it finish.   

grow extended partition sda2  to fill the unallocated space. (will still be unallocated, but now inside sda2. 

grow sda5 to fill the unallocated space. press apply - go to a movie it will take a while.

Last but not least fix GRUB - the stage2 file has move so need to rebuild the mbr code.
at a terminal window.
```
grub
or depending on which live CD your using 
sudo grub
```then at the grub> prompt
```
root (hd0,4)
setup (hd0)
quit

```and your done. enjoy


> **Warren Watts said:**
> Oops!...

Me too  :shock:  only this time i remembered.

---

### Post by johnnydotexe on 2009-08-25
> **louieb said:**
> create unallocated space by shrinking sda1 (your windows partition). press apply, when done reboot and make sure windows still works - it will probably want to run chkdisk on 1st reboot - let it and let it finish.   

grow extended partition sda2  to fill the unallocated space. (will still be unallocated, but now inside sda2. 

grow sda5 to fill the unallocated space. press apply - go to a movie it will take a while.


Maybe I misunderstood something, but what you just typed doesn't seem to add up...

1.  I have no unallocated space, so I need to create some unallocated space by reducing the size of the sda1 partition.  Easy enough.

[B]2.  I increase sda2 to fill the unallocated space?  This leaves me with no more unallocated space.

3.  I increase sda5 to fill the unallocated space...but I can't because step 2 used up the unallocated space.[/B]

Did I misread something?

---

### Post by louieb on 2009-08-25
You missed sda2 is an **extended partition**. if you look at Gparted you'll see it wraps around **logical partitions** sda5 and sda6. 

Extended partitions were invented to to be able to have more that 4 partitions on a hard drive.  An extend partition is a container that defines a area of the hard drive. Inside the extended partition are logical partition(s).

[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by johnnydotexe on 2009-08-25
I was able to resize sda1 down, rebooted and ran chkdsk with no issues.

It won't let me do anything to sda2, has the two keys on it which I'm assuming means it is locked.  I am logged in as a "live session user" from the liveCD.  It will let me make changes to sda5 from the looks of it, sda2 and sda6 are the only two that are locked.

---

### Post by louieb on 2009-08-25
The live CD is using the swap partition. (Thats normal most live CDs will use the swap partition if it finds one) right click on it and select **swapoff**. 
That should remove the locks.

---

### Post by johnnydotexe on 2009-08-25
Ok...the boot order change worked, simply moved the windows lines to between those above mentioned lines.  Commented out the "other operating systems line" as well.  Also successfully increased the partition.

New problem, not sure when it started...possibly after I increased the extended partition and the main logical partition.  Boot order list is messed up.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=829745d2-815b-4ec2-88c7-5d9b01201ff2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=829745d2-815b-4ec2-88c7-5d9b01201ff2

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        829745d2-815b-4ec2-88c7-5d9b01201ff2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=829745d2-815b-4ec2-88c7-5d9b01201ff2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        829745d2-815b-4ec2-88c7-5d9b01201ff2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=829745d2-815b-4ec2-88c7-5d9b01201ff2 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        829745d2-815b-4ec2-88c7-5d9b01201ff2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=829745d2-815b-4ec2-88c7-5d9b01201ff2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        829745d2-815b-4ec2-88c7-5d9b01201ff2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=829745d2-815b-4ec2-88c7-5d9b01201ff2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        829745d2-815b-4ec2-88c7-5d9b01201ff2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
```

As you can see it goes...

windows
ubuntu
ubuntu recovery
ubuntu
ubuntu recovery

...why is it doing this now, and how do I fix that?

---

### Post by louieb on 2009-08-25
Don't worry about it. The extra Ubuntu entries were created with the last Kernel Update.  You can comment out the older kernel or use Synaptic to remove it. I usually don't bother to do either.  In fact it is suggested to keep one or two old kernels just in case you have problems with the new. 

> 
title        Ubuntu 9.04, kernel 2.6.28-[COLOR=Red]15[/COLOR]-generic
title        Ubuntu 9.04, kernel 2.6.28-[COLOR=Red]11[/COLOR]-generic


---

### Post by johnnydotexe on 2009-08-25
So if I wanted to, I could safely comment out the .11 versions and leave the .15 versions?  I may do that just to clean up the boot menu a little.

---

### Post by louieb on 2009-08-25
Thats right the -11- kernel is the older.

---

### Post by AlexanderDGreat on 2009-08-26
Or if you want uncomment hiddenmenu - so boot grub won't bother you forever - plus, faster boot time.

---

### Post by johnnydotexe on 2009-08-26
> **AlexanderDGreat said:**
> Or if you want uncomment hiddenmenu - so boot grub won't bother you forever - plus, faster boot time.

What exactly will this do?

---

### Post by AlexanderDGreat on 2009-08-29
You will no longer be shown the grub menu boot list in your master boot record.

So whatever's the default OS, it will be loaded automatically, anyhows, you can comment it again if you prefer choosing the OS or kernels.

It says... "Hides the menu by default (press ESC to see the menu)".

While "timeout" is the amount of time in seconds to choose OS or kernel.

=)

---

### Post by DeMus on 2009-08-29
> **johnnydotexe said:**
> 1.  I am running Ubuntu 9.04 alongside of Win XP Pro on an 80GB HDD, on my laptop.  The Ubuntu Updater is teling me it needs xxx space to download and install the updates, so which Ubuntu partition needs to be increased?  How do I decrease the windows partition and increase whatever Ubuntu partition if all of them appear to be locked?

2.  When I boot up my computer, I want it to default to windows instead of Ubuntu if I don't pick an option myself within X amount of time, like it does now except vice-versa.  Can this be changed?

3. I plan on buying a new 320GB HDD for this laptop.  If I buy the laptop-HDD adapter to hook them up to my desktop, can I copy the contents of the 80GB over to the 320GB with something like Acronis True Image?  Or is there an easier way, or better software to accomplish this task?

1)
Boot your computer from the Ubuntu CD and choose the live CD version. Once booted open Nautilus file manager and unmount all disks you see by right clicking on them and choose unmount. Start gparted and decrease the window partition and increase the / (root) Ubuntu partition.

2)
In /boot/grub/menu.lst you _**do not**_ change the order in which the OS's are mentioned. You only look at the list and determine which number in the list is your windows OS.
On top of the file you see a line with the text: default  0
Change the 0 into the number for Windows.
You can change the file by opening a terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```

3)
What do you plan to do with the new HDD? Will that be your only HDD or will you keep the 80GB disk for software and the new disk for data?

---

### Post by johnnydotexe on 2009-08-29
Already got what I needed from some above posters, but thanks for the reply.  I need all the info I can get, gotta make it over this linux-learning curve so I can make the full switch from winblowz.  In regards to not re-arranging the boot list...several above instructed me to do so and I did, and it worked fine...wasn't aware that I shouldn't have done that.  I'll make a note of your instructions and use those next time since they seem easier/safer for an ubuntu noob like me.  I plan on dual-booting ubuntu on the desktop now that this laptop is getting sold, so the advice is appreciated. :)

---

