---
title: "Hide Unmounted Partitions"
date: 2009-10-29
forum: General Help
---

### Post by Akavashi on 2009-10-29
Hey guys,
Just installed a fresh copy of Ubuntu Karmic Koala! OZZIE, OZZIE, OZZIE!
Now, my only problem is that I have an unmounted Windows 7 System Reserved Disk (dev/sda2), the unmounted main Windows partition (dev/sda3) and the floppy drive showing in Gnome, ready to be mounted.
How would I hide them, to stop myself accidentally mounting them?

I've tried blacklisting the floppy [http://ubuntuforums.org/showthread.php?t=616153](http://ubuntuforums.org/showthread.php?t=616153) - and hiding the windows partitions [http://ubuntuforums.org/showthread.php?t=905859](http://ubuntuforums.org/showthread.php?t=905859). But by my understanding, Karmic has moved away from HAL and are now using DeviceKit and so the latter is outdated. :(

So any help, would be greatly appreciated! :p Cheers guys!

---

### Post by ezanium on 2009-11-04
under Karmic 9.10, HAL is replaced by DeviceKit-Disk for block devices. 
you have to set the "presentation hide" property on the block device you want to hide in Nautilus for example.

based on /lib/udev/rules.d/95-devkit-disks.rules, create a file under /etc/udev/rules.d/ to set it.

here is an example:
$ sudo vi /etc/udev/rules.d/hide-partitions.rules
> # we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

##############################################################################

# Partitions which desktops should not display
ENV{ID_FS_TYPE}=="ntfs|vfat", \
 ENV{ID_FS_LABEL}=="VISTA|HP_TOOLS", \
  ENV{DKD_PRESENTATION_HIDE}="1"

##############################################################################

LABEL="hide_partitions_end"review block disk information with:
$ devkit-disks --dump | less

---

### Post by Akavashi on 2009-11-04
Hey Hey, cheers for the help Ezanium,
I've got it all working :D but...
Now my dvd drive doesn't show up :S lol >.< *slaps own face* I looked at the 95-devkit-disks.rules file in lib, and inserted my own code to hide the Floppy.

It does hide my two partitions (52 GB Filesystem, System Reserved) and the floppy drive... just also the DVD drive... :/

As shown here:
```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

# Partitions which desktops should not display
ENV{ID_FS_TYPE}=="ntfs|vfat",
ENV{ID_FS_LABEL}=="52 GB Filesystem",
ENV{DKD_PRESENTATION_HIDE}="1"

# Partitions which desktops should not display
ENV{ID_FS_TYPE}=="ntfs|vfat",
ENV{ID_FS_LABEL}=="System Reserved",
ENV{DKD_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end"
```

Any Ideas? Cheers, sorry to be a bummer

---

### Post by Akavashi on 2009-11-05
Okay, well... Looked further into the 95-devkit file like before, and found that you can just hide partitions and devices etc directly through their partition mount location (eg /dev/sda*)
So here's the code that I used to hide my partitions and the floppy drive completely from gnome:
```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda2 that we want to hide from gnome
KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda3 that we want to hide from gnome
KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end" 
```
Cheers for the help again Ezanium! Thought I'd post up the code that I figured out with your help, just for others... I'll try and mark as solved (kinda a newbie to posting on this forum...)

---

### Post by Kartinka on 2009-11-14
> **Akavashi said:**
> Okay, well... Looked further into the 95-devkit file like before, and found that you can just hide partitions and devices etc directly through their partition mount location (eg /dev/sda*)
So here's the code that I used to hide my partitions and the floppy drive completely from gnome:
```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda2 that we want to hide from gnome
KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"

# Partition sda3 that we want to hide from gnome
KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end" 
```Cheers for the help again Ezanium! Thought I'd post up the code that I figured out with your help, just for others... I'll try and mark as solved (kinda a newbie to posting on this forum...)

Hey Community ;),

I'm new here and new by using Ubuntu. in the last days, I tried to install Ubuntu 9.10 and make some settings there. No long time later, i found the first problems for myself...

I have the following partitions on my only hard drive in my Laptop.

[FONT=Times New Roman][FONT=Arial]40 GB Vista Systempartition
20 GB Ubuntu / (root) Partition
2  GB Ubuntu SWAP
10 GB Ubuntu /home Partition
30 GB Filepartition for Vistasystem
70 GB Filepartition for Vistasystem
80 GB Filepartition for Vistasystem[/FONT]
[FONT=Arial]
While i tried to seperate both Systems of each other I found this Thread. Because I will seperate them that 
I will see nothing of Windows in Ubuntu and otherwise.[/FONT]
[/FONT]I tried it with the written things in this Thread and everything happend good, I was able to hide the Partitions.

But now I have some little questions.

First question: Are the partitions hidden from the whole system with that code or only from gnome / nautilus?!

Second question is for understanding the code:

What are the following words do, and where can i find a description or manual with them?!

ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

ENV{DKD_PRESENTATION_HIDE}="1"

I searched but nowwhere i found something about that?! But anyway I have to found or? Because how to know something abaut add|change or loop*|ram* to write that code when it's nowwhere to read?!

---

### Post by Akavashi on 2009-11-15
Hey Kartinka,
Yup, you're quite right, they are hidden away from Gnome/Nautilus... as you can still see them in the Disk Utility located under Administration.
And the code... I have no idea about the ACTION, SUBSYSTEM and that KERNEL would search through the kernel for hardware.
And the ENV{} command envelops a certain tag to that hardware...
Those are my first impressions of what those commands do though, so maybe someone will clarify for you later... Hope that kinda helps, couldn't find a decent guide on the interwebs except for this manual [http://hal.freedesktop.org/docs/DeviceKit-disks/]("http://hal.freedesktop.org/docs/DeviceKit-disks/").

---

### Post by pt123 on 2009-12-11
this is awesome I have been looking for a way to do this, as I am currently on Jaunty which uses hal. 

[http://ubuntuforums.org/showthread.php?t=1216790](http://ubuntuforums.org/showthread.php?t=1216790)

---

### Post by BrowneR on 2009-12-30
> **Kartinka said:**
> 
Second question is for understanding the code:

What are the following words do, and where can i find a description or manual with them?!

ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"


This is explained on the udev manpage:

```
man udev
```

> **Kartinka said:**
> 
ENV{DKD_PRESENTATION_HIDE}="1"


This is explained in the device kit man page:

```
man DeviceKit-disks
```

Hope that helps you out as I just had to look all that up myself! :)

Chris

---

### Post by Morbius1 on 2009-12-30
Good lord,

> Now, my only problem is that I have an unmounted Windows 7 System Reserved Disk (dev/sda2), the unmounted main Windows partition (dev/sda3) and the floppy drive showing in Gnome, ready to be mounted.
How would I hide them, to stop myself accidentally mounting them?sudo mkdir /Windows/sda2
sudo mkdir /Windows/sda3

Add the following lines in /etc/fstab:
/dev/sda2 /Windows/sda2      ntfs    defaults,umask=777    0    0
/dev/sda3 /Windows/sda3      ntfs    defaults,umask=777    0    0

It won't show up under "Places" in nautilus, it won't show up on the desktop, and with umask=777 not even root will be able to touch it.

Badda - Bing.

You got me on the floppy. Don't put a floppy in it would be my first suggestion.:)

---

### Post by Akavashi on 2010-01-01
Yeah... that's the thing, I don't have a floppy drive lol
My bios is reporting that I have one for some reason though, and i can't waver it's little decision on that...
And cheers for the easier way to do this Morbius1 :P
P.S. Happy new year!

---

### Post by mbudden on 2010-01-05
> **Morbius1 said:**
> Good lord,

sudo mkdir /Windows/sda2
sudo mkdir /Windows/sda3

Add the following lines in /etc/fstab:
/dev/sda2 /Windows/sda2      ntfs    defaults,umask=777    0    0
/dev/sda3 /Windows/sda3      ntfs    defaults,umask=777    0    0

It won't show up under "Places" in nautilus, it won't show up on the desktop, and with umask=777 not even root will be able to touch it.

Badda - Bing.

You got me on the floppy. Don't put a floppy in it would be my first suggestion.:)

How do you add the lines in /etc/fstab:? Sorry I'm a noob at this lol. I've been trying to do this forever.

---

### Post by dcstar on 2010-01-05
> **Morbius1 said:**
> 

Add the following lines in /etc/fstab:
```
/dev/sda2 /Windows/sda2      ntfs    defaults,**noauto**,umask=777    0    0
/dev/sda3 /Windows/sda3      ntfs    defaults,**noauto**,umask=777    0    0
```

man fsck:
**noauto** Can only be mounted explicitly (i.e., the  -a  option  will  not cause the file system to be mounted).

---

### Post by Akavashi on 2010-01-06
mbudden you add the lines by typing in terminal:
```
sudo gedit /etc/fstab
```
And dcstar, this is a question about how to hide certain partitions altogether in gnome/Ubuntu... not just to stop it from auto-mounting.

---

### Post by Morbius1 on 2010-01-06
> Quote:
                                                                      Originally Posted by [quote]**Morbius1**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8583069#post8583069")                 
                 [I]
Add the following lines in /etc/fstab:
     Code:
     /dev/sda2 /Windows/sda2      ntfs    defaults,**noauto**,umask=777    0    0
/dev/sda3 /Windows/sda3      ntfs    defaults,**noauto**,umask=777    0    0 
[/I]man fsck:
**noauto** Can only be mounted explicitly (i.e., the  -a  option  will  not cause the file system to be mounted).
> **dcstar said:**
> man fsck:
**noauto** Can only be mounted explicitly (i.e., the  -a  option  will  not cause the file system to be mounted).
[/quote]I'd appreciate it if you didn't quote me with your modifications, If I had wanted the noauto option I would have placed it there myself.

Akavashi,

Not to be nit pickey but I'd recommend **gksu gedit /etc/fstab**

sudo for command line
gksu for GUI applications

It's not that it won't work, it's just that I have experienced bad things when using sudo with GUI apps.

---

### Post by Akavashi on 2010-01-07
lol ah k, sorry about that, I've never been in the habit of using gksu... Cheers for the tip, I'll remember that :P
Turns out you learn heaps of new things every day when using Ubuntu :D

---

### Post by Akavashi on 2010-01-07
So in the final days of this thread, I reinstalled Ubuntu again with all of the windows partitions hidden using Morbius1's neat little post: :P
(Edited, 'cause mkdir doesn't handle linked directories, only makes single directories at a time)

> **Morbius1 said:**
> 
cd /
sudo mkdir /Windows
cd /Windows
sudo mkdir sda2
sudo mkdir sda3

then

gksu gedit /etc/fstab

Add the following lines in /etc/fstab:
/dev/sda2 /Windows/sda2      ntfs    defaults,umask=777    0    0
/dev/sda3 /Windows/sda3      ntfs    defaults,umask=777    0    0

It won't show up under "Places" in nautilus, it won't show up on the desktop, and with umask=777 not even root will be able to touch it.


Just remember that you change sda2 and sda3 according to how your partitions are set up, and for the Floppy... I just used the grotty devicekit way... *vomits*
Go to /etc/udev/rules.d/ and make a blank file named "hidden-floppy.rules"
and enter in this code into the file, and save:
```
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Floppy Drive which should not display
KERNEL=="fd0", ENV{ID_DRIVE_FLOPPY}="1", ENV{DKD_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end"
```[FONT=monospace]
Thanks to Ezanium and Morbius1 for all of their help with this problem :P
[/FONT]

---

### Post by Morbius1 on 2010-01-07
> (Edited, 'cause mkdir doesn't handle linked directories, only makes single directories at a time)Quite right. Appreciate the correction. I always create the /Windows directory during an initial install and then add mount points at a later date after I decide how I want to mount them. I got sloppy again :redface:

---

### Post by Akavashi on 2010-01-08
Haha, no worries mate! Pretty sure I gave out dodgey advice with the mix up between **sudo** and **gksu** anyway, so I appreciate your help too. :P

---

### Post by pt123 on 2010-08-27
Using this 
sudo gedit /etc/udev/rules.d/hide-partitions.rules
was working fine in Karmic, but in Lucid it is not

Edit:
in Lucid DKD_PRESENTATION_HIDE was changed to 
UDISKS_PRESENTATION_HIDE

[http://fedoraforum.org/forum/showthread.php?t=250263](http://fedoraforum.org/forum/showthread.php?t=250263)

It is all working now when using UDISKS_PRESENTATION_HIDE

---

### Post by mikewhatever on 2011-11-07
The 'udev rule' method works well with all the *buntus. Here is an example:
> ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Let's hide sda1 and sda3
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"
KERNEL=="sda3", ENV{UDISKS_PRESENTATION_HIDE}="1"

################################################## ############################

LABEL="hide_partitions_end"


---

### Post by ahso4271 on 2011-11-07
Hmm how could I show all partitions etc in 10.04?
This is very handy for not going to device manager and simply click.
Thanks

---

