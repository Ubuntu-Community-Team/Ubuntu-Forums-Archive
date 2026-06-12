---
title: "Ubuntu OS Won't Boot Up"
date: 2010-04-22
forum: General Help
---

### Post by Kid Charlemagne on 2010-04-22
My computer won't boot up from the installed version of Ubuntu. I was running 8.04 with no problems, but it stopped working after entering a command code to fix the limit for virus definitions on Avast. I removed the code, but now on boot up all I get is a blank screen and blinking cursor.

I can boot up with an Ubuntu 9.1 live disk, and it shows the installed version of Ubuntu and all my data are still there. Is there a way to do a general repair, that will enable my computer to boot up from the installed operating system?

---

### Post by P4man on 2010-04-22
can you give us some more information on what you did exactly that hosed your 8.04 ? Also, when you try and boot from the hdd, do you get grub menu at least, or not even that?

---

### Post by Kid Charlemagne on 2010-04-22
The computer stopped booting up after one line of code was entered in the terminal. I subsequently removed the code, as stated previously, with no result. I'm new to linux, so I don't really know how to navigate to the grub menu.

---

### Post by P4man on 2010-04-22
> **Kid Charlemagne said:**
> The computer stopped booting up after one line of code was entered in the terminal. 

With one line of code you can format your drives beyond repair. Not saying thats what you did (since you can still access the files), but it would help a lot if we had a clue what that line was. Did you follow instructions on a webpage, do you still have the link? Vaguely remember what it was you were trying to achieve?
> 
I subsequently removed the code, as stated previously, with no result. I'm new to linux, so I don't really know how to navigate to the grub menu.

But you still do get a grub a menu? In that menu there should be a "recovery mode" option. Have you tried that?

---

### Post by Kid Charlemagne on 2010-04-22
Avast apparently had set a low limit on the amount of virus definition updates it was capable of holding, so I was advised to go to this thread, 
[http://ubuntuforums.org/showthread.php?t=1448803](http://ubuntuforums.org/showthread.php?t=1448803), and enter the following code as per instructions below.

1) open the terminal
2) a)type this command to open the file you need to edit:
Code:

sudo gedit /etc/init.d/rcS

b) type your password and hit enter

3) when the text file opens add the line:

Code:

sysctl -w kernel.shmmax=128000000

4) make sure the line you added is before:

Code:

exec /etc/init.d/rc S

5.- This is how it should look like:
Code:

 #! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S

6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%

It didn't work, and actually prevented the computer from booting up. So I burned a Live CD, and chose the option to use without installing. Then I
found the terminal and used the command code gksudo nautilus to access the installed operating system. I removed the offending code, but my computer still wouldn't boot up.

Being new to Linux I don't know what a grub menu is, or how to navigate to it. Any information you would provide in helping me resolve this problem would be greatly appreciated. I've shown the code to other Linux people and no one thinks it is malicious.

---

### Post by Calash on 2010-04-22
Double check and make sure the file looks like the following

```

#! /bin/sh
#
# rcS
#
# Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
#

exec /etc/init.d/rc S

```

Also, if you check the permissions of that file they should be the following


```

-rwxr-xr-x 1 root root 117 2009-09-07 14:58 /etc/init.d/rcS

```

---

### Post by P4man on 2010-04-22
I dont think its malicious either, but on linux its very easy to make a typo and that might have far reaching effects if you are unlucky. You may just have missed a space or mixed uppercase/lowercase somewhere. Linux is case sensitive in case you didnt know.

Maybe you can post the contents of the rcS file ? Perhaps you overlooked something trivial.

As for grub; grub is the bootloader. If you power on your machine, you will first get the BIOS post screen of your motherboard. Then the screen goes black, and shortly after you usually get grub menu, which looks like this:

[http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg](http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg)

In some cases, instead you get a message for a few seconds saying "press escape to view grub menu" or something along these lines.

Are you seeing anything like that? (and did you before this happened?)

---

### Post by Kid Charlemagne on 2010-04-22
How do you check the permissions?

---

### Post by Kid Charlemagne on 2010-04-22
I think I can get the bios menu by hitting the number 2 before the machine tries to boot up. But it is a series of about five tabs, none of which, I think, constitute the grub menu.

---

### Post by P4man on 2010-04-22
So you've never seen such a menu, or a 3 second prompt telling you to "press escape to enter grub" on that machine? One or the other usually comes up automatically right after bios post, unless grub is configured to be silent (which isnt the default afaik).

Im just trying to figure out if its trying to boot ubuntu at all.

---

### Post by P4man on 2010-04-22
> **Kid Charlemagne said:**
> How do you check the permissions?

From a terminal, using the live cd, first cd to the correct folder (after mounting the drive, so accessing it). something like

```
cd /media/yourharddisk/etc/init.d
```

then 

```
ls -l rcS
```

Alternatively, launch nautilus and browse to it like you did earlier. Right click it, properties, permissions. Should look like this:

[[img]http://www.ubuntu-pics.de/thumb/53606/screenshot_001_p9Op93.png[/img]](http://www.ubuntu-pics.de/bild/53606/screenshot_001_p9Op93.png)

be sure to do this on your harddrive and not the livecd filesystem

---

### Post by Kid Charlemagne on 2010-04-22
I just double checked the file, and it looks exactly like your post said it should - right down to the spaces.

---

### Post by Kid Charlemagne on 2010-04-22
I've never seen that menu. I'm running Ubuntu 8.04 on a Dell Inspiron 9 netbook.

---

### Post by Kid Charlemagne on 2010-04-22
Thanks for the detailed instructions. Let me get back to you after trying this. Thanks for all the help. It is most appreciated.

---

### Post by P4man on 2010-04-22
> **Kid Charlemagne said:**
> I've never seen that menu. I'm running Ubuntu 8.04 on a Dell Inspiron 9 netbook.

Thats the ubuntu that came preinstalled? I bet Dell hid the grub menu then, that would explain. Anyway, check permission on that file. It should be owned by root and be executable. If it is correct, we'll have to dig a bit deeper.

---

### Post by P4man on 2010-04-22
BTW, I just noticed in the post where you took the instruction from, they told you to enter "sudo gedit". This is a mistake, it should be "gksudo gedit". What you did can cause problems with file system permissions. I wouldnt expect those to render ubuntu completely dead, I would expect error messages instead, but maybe its related (I posted in that thread asking to correct it).

---

### Post by Kid Charlemagne on 2010-04-22
cd /media/yourharddisk/etc/init.d

This is coming back no such file or directory.
My permissions on the rcS folder look totally different than your screen shot.

---

### Post by Kid Charlemagne on 2010-04-22
It did come preinstalled. If worse comes to worse I have a recovery disk, but then I lose everything I had on the computer. The owner on the rcS file is root; it looks executable. What next?

---

### Post by P4man on 2010-04-22
Next, I hope someone else is gonna chime in and give you the actual solution lol.

Anyway, first, lets make sure you looked at the right file. What was the location?
If it was in 

/etc/init.d/

then it wasnt the one on your harddisk! It should be in

/mnt/somethingdontknowwhat/etc/init.d or
/media/somethingdontknowwhat/etc/init.d 

I obviously dont know the exact location, it depends on your setup. It could /media/disk/etc/init.d or something else.

Can you make very sure you checked the file on the harddisk, and not the one in your current live file system?

If you are sure about that, lets have a look at the log files. Browse to 

/mnt/somethingdontknowwhat/var/log

Show details, order by date. Look at the most recent ones. Can you check the timestamp, is it when you last tried booting, or from before you hosed your system? Perhaps attach "syslog" and "messages" or copy paste the last lines from either ?  Again be very sure its from the ubuntu harddisk, not the live session.

---

### Post by P4man on 2010-04-22
Im off for tonight. If its not solved tomorrow, if you like, I can log in to your machine remotely (assuming its connected to the internet from the livecd?).

For that, easiest is you download this tiny little app:
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

(click on ubuntu and install. It should install during a livecd session, but obviously each time you reboot it will be gone again)

You will need my IP address, Ill send you a PM tomorrow.  with that you just click on "get help", enter my IP and I can have a look at your machine. If you'd rather not, then no worries, we'll try through the forum.

---

### Post by Kid Charlemagne on 2010-04-22
It was definitely on the hard drive because I saw the code I had entered, deleted it, and then saved. Before that instead of a blank screen when trying to boot up; that code was referenced with an error message. The computer wouldn't boot, but it would list the following repeatedly: "error: "kernel.shmax" is an unknown key". Now I just get a blank screen with a cursor. Let me try to look at the log files and get back to you.

---

### Post by Kid Charlemagne on 2010-04-22
I'm getting no such file or directory with these codes. I must be doing something wrong.

---

### Post by P4man on 2010-04-23
With what codes? If you actually typed in :somethingdontknowwhat: then that doesnt surprise me! Its just that I dont the know the actual path, the idea is that you replace it with the correct one for your machine.

Okay, do this: open nautilus and browse to your harddisk and then your home folder and then your username. Make sure you see the personal files on your harddrive that you know are on there. 

Now press control+L and nautilus will reveal the actual path. Copy paste that here, so I can use the actual path to avoid confusion.

---

### Post by Kid Charlemagne on 2010-04-23
I didn't type in somethingdontknowwhat, but with my knowledge base that was a definite possibility! I tried to locate the actual pathway by entering fdisk -1 in the terminal. It came back as dev/hda7 for my hard disk. Alas, when I entered that pathway along with the appropriate code; it came back no such file or directory.

I noticed when I open nautilus, that I can only access the live CD folders with the root browser. Someone I previously consulted said to ignore the error messages that I get as long as the root browser window opens. It should give me permission to access the files and folders on the installed OS.

I can navigate to the 15GB file system, which is my internal flash drive by using the places menu on the live desktop. When I access it, all my files are still there and functional. It lists the pathway as /media/ceab9ccf-1327-43b3-b20f-33932bc0999d/home/thomas. When I use that pathway; it is still coming back no such file or directory though. So I can't get any more information. With no logs it might be hard to pin down what is causing the problem. Is there some kind of general repair I can do?

---

### Post by P4man on 2010-04-23
> I noticed when I open nautilus that I can only access the live CD folders with the root browser. Someone I previously consulted said to ignore the error messages that I get as long as the root browser window opens. It should give me permission to access the files and folders on the installed OS.

I think you are confusing a few things. But what I remember from ubuntu 8.04, it will not mount the harddisks automatically, unless you click it first from "Places" (or you enter the correct mount command). Then it gets mounted, and you can browse to it. If you dont know what mounting is, read on ->

> **Kid Charlemagne said:**
> 
I can navigate to the 15GB file system, which is my internal flash drive by using the places menu on the live desktop. When I access it, all my files are still there and functional. It lists the pathway as /media/ceab9ccf-1327-43b3-b20f-33932bc0999d/home/thomas. When I use that pathway; it is still coming back no such file or directory though. So I can't get any more information. With no logs it might be hard to pin down what is causing the problem. Is there some kind of general repair I can do?

A few things, basically background and FYI. /dev/sda is a harddisk (the first one, the second is /dev/sdb).  

/dev/sda1 is the first partition of that harddisk.  But its the "device", not the logical filesystem. A partition editor would use those, and would use it regardless if its a windows, Linux, swap or whatever filesystem on it, or none at all.  If you switch drives (on a desktop system) or add partitions, those names would also change, as it points to first or second drive or partition.

But you cant browse /dev/sda1 to see files. For a partition to be browseable (if thats a word), it needs to be "mounted" to a mountpoint. That means the OS must load (and understand) the filesystem used on that partition. Then you can see files on it. 

In your case, the live session mounts it to:

/media/ceab9ccf-1327-43b3-b20f-33932bc0999/

(newer ubuntu releases thankfully use shorter names lol).

Anyway, The log files ought to be in 

/media/ceab9ccf-1327-43b3-b20f-33932bc0999/var/logs

Its possible you have to make it mount the drive by clicking it from the places menu, or from nautilus. Its been a few years since I used hardy.

Then, if you want to browse there from the terminal, use tab completion. Type

cd /media/ce *[COLOR="Lime"]<press TAB key>[/COLOR]*
It will complete the rest. If more than one possibility exist, press tab twice to see a list of possibilities. Works in most places.

> Is there some kind of general repair I can do? 

yeah, from the grub menu, which Dell hid from you. Could be easy to change that. Can you post the contents of:

/media/ceab9ccf-1327-43b3-b20f-33932bc0999/boot/grub/menu.lst ?

---

### Post by Kid Charlemagne on 2010-04-23
It is still coming back no such file or directory.

---

### Post by P4man on 2010-04-23
It says that doing what exactly? 
Anyway, this is taking a fair bit of time this way and nothing much gets done. The gitso offer (remote access) still stands, assuming the machine is connected to the internet (in which case, it would also be nice if you copy/pasted the output of what you are trying).

---

### Post by Kid Charlemagne on 2010-04-23
I tried to get the grub menu, but it came back on such file or directory. I'm not networked with the Live CD.

---

### Post by P4man on 2010-04-23
are you doing this in nautilus, or from the console? 
Is there at least a 
/media/ceab---etc---/boot 
folder?
Does it have a grub subfolder?
Are you sure there is no menu.cfg in there?

---

### Post by Kid Charlemagne on 2010-04-23
Not sure if this helps, but I navigated to the folder manually and copied the contents. Please see below:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
## e.g. in_domU=detect
##      in_domU=true
##      in_domU=false
# in_domU=false

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-24-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-24-lpia

title		Ubuntu 8.04.2, kernel 2.6.24-22-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-22-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-22-lpia

title		Ubuntu 8.04.2, kernel 2.6.24-19-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-19-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-19-lpia

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by P4man on 2010-04-23
> **Kid Charlemagne said:**
> Not sure if this helps, but I navigated to the folder manually and copied the contents. Please see below:

You may want to do the same to browse  "manually" to the log file folder, and post the log files.

As for grub, try these 2 little changes; set the time out to 5 and comment out the line with hiddenmenu. you will have to edit the file with root permissions, so if you are doing this through nautilus, then start nautilus as root (gksudo, unless Dell interface has a link for it). 

if you are doing this through the command line, browse to the folder, and enter 

```
gksudo gedit menu.lst
```

(gedit being the text editor).

Changes marked in green:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="green"]timeout		**5**[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="green"]**#** hiddenmenu[/COLOR]

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
## e.g. in_domU=detect
##      in_domU=true
##      in_domU=false
# in_domU=false

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-24-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-24-lpia

title		Ubuntu 8.04.2, kernel 2.6.24-22-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-22-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-22-lpia

title		Ubuntu 8.04.2, kernel 2.6.24-19-lpia
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled quiet splash
initrd		/boot/initrd.img-2.6.24-19-lpia
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-lpia (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd		/boot/initrd.img-2.6.24-19-lpia

### END DEBIAN AUTOMAGIC KERNELS LIST
```

After doing that, try booting the machine from the hdd again. You will hopefully get to see the grub menu now with the "recovery mode" as option.

---

### Post by Kid Charlemagne on 2010-04-23
On the second change I should just add a # symbol before hidden?

---

### Post by P4man on 2010-04-23
Yes. It comments it out, so the line is ignored. (and you can later delete that sign again to hide the menu again if you want)

---

### Post by Kid Charlemagne on 2010-04-23
Sweet! I made the changes and I get a grub menu now. It looks like there are three recovery modes to chose from, with different kernels. What should I do next?

---

### Post by P4man on 2010-04-24
I dont remember the options hardy gave you, but feel free to experiment a bit at this point and tell us what happens. For instance, if you select a different (older) kernel in that list, does it boot to the desktop? If not, do you get an errror message?

If you try the recovery mode, Id go for the "xfix" first (or whatever they call it to reconfigure X windowing system) If thats no help,  Id like to know if the root terminal works. If that works, then at least we can easily access your log files and see whats going on.

Last question, can you connect the machine to a wired network temporarily? That would make it a lot easier to try some repairs from a root terminal, by reinstalling default packages.

---

### Post by Kid Charlemagne on 2010-04-24
Before I try the recovery mode; I think I can get the log files for you to look at. There are daemon logs, auth logs, kern logs. Not sure what files you need in order to diagnose the problem. 

I have access to a wireless network, but it doesn't seem to want to connect to it from the live CD. Maybe I can somehow get it to connect by accessing the installed OS.

---

### Post by Kid Charlemagne on 2010-04-24
When the grub menu comes up it looks like these are my three choices:

title Ubuntu 8.04.2, kernel 2.6.24-19-lpia (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd /boot/initrd.img-2.6.24-19-lpia


title Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd /boot/initrd.img-2.6.24-22-lpia



title Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-24-lpia ro root=UUID=ceab9ccf-1327-43b3-b20f-33932bc0999d hpet=disabled single
initrd /boot/initrd.img-2.6.24-24-lpia

Would you go with 19, 22 or 24? Do you want to see the logs first? Thanks again. You are very patient.

---

### Post by P4man on 2010-04-25
Those are just different kernels. You could try any of them. Booting an older kernel can help if a kernel upgrade broke something; in your case the problem is not likely kernel related, so it really doesnt matter. Go ahead and try.

That said, in the time this thread has been running, you could have made a backup of your home folder to an usb stick and reinstalled ubuntu 10x over. If you are taking this as an opportunity to learn, then lets keep going, if you just want to fix the thing, copy your homefolder and reinstall from the cd.

---

### Post by Kid Charlemagne on 2010-04-25
I think I'll try recovery mode just out of curiosity. The ultimate goal was to fix my computer, but I felt like I learned a lot as well. So thanks for all the knowledge, effort on my behalf and patience.

If the recovery mode doesn't work for me; I guess I just mount the hard disk, drag the home folder to a USB stick, reinstall from the Dell Ubuntu disk, and then I'm not quite sure. 

Maybe the newly installed OS has a blank home folder that I replace with the one I put on the USB stick? Let me know, and I guess we can call it a day. Can't thank you enough for all the help. Really appreciate it.

---

### Post by P4man on 2010-04-25
If you are under no time pressure to get the machine up and running again, then answer the questions in post 35 (those that havent been answered yet). Its only now that we can actually begin looking for the cause (especially if the root terminal  in recovery mode works). Then you can access the log files and we might get somewhere.

As for restoring the home folder. If you do a fresh install, there will be a /home created with a subfolder for you username, and that is your homefolder:
/home/yourname
The installation procedure will ask you for a username, probably best you use the same name as you are using now. After installing, Id boot from the live cd and copy your backed up home folder over the newly created one. After that, you may have to fix the ownership on the files (im not sure, but they might be owned by "root" or "ubuntu" if you copy from a livecd session. If so, you can do that by running this in a terminal:

sudo chown -hvR [COLOR="Red"]user[/COLOR] /home/[COLOR="Red"]user[/COLOR]

replacing "users" with your username.

But again, if you're not stressed for time, lets see if we cant fix your install and learn some things along the way :)
(not too mention, find out what caused all this in the first place)

---

### Post by Kid Charlemagne on 2010-04-25
No time pressure, but I didn't want to wear you out with this. Wondering why I need to boot from the Live CD. Won't the system boot up with factory defaults when I use the recovery disk that came with the computer? The home folder with all my data will have previously been stored on the USB stick. Not sure how I would get the contents of the old home folder into the new home folder. If I drag and drop I get a folder within a folder.

I can get the log files, but I'm not sure which ones you need. In a previous post I mentioned that there are log files marked daemon, auth and kern. At least they seem to be log files to me, but I could definitely be wrong.

I'd like to keep working to see if we can fix the install and, as you noted, hopefully learn some things along the way.

I tried the different recovery modes, but they didn't seem to do much. Then again I have no idea what I am looking for. It looked like a bunch of code spit out and the last line said done. It doesn't seem like you can even read a lot of it because when you arrow up or down symbols come out, instead of paging up or down.

---

### Post by P4man on 2010-04-26
I need a lead here... I have no idea whats happening.
When you try to boot normally, is there any error message? If it stops booting, does pressing control+alt+F1 show anything?

If not try this; in the grub menu, select the normal option, but rather than pressing enter, press E to edit. select the line with the kernel and edit it (press E again). At the end remove "quiet" and "splash" if they are present. Enter to confirm that line, and then press B to boot. (some screenshots here: [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation))

the idea here is that we make the boot process more verbose. No fancy screens but information on screen while it boots. Can you tell me where it stops? Whats on the screen?


Last thing to do; if a normal boot fails and the above doesnt give any hints, boot in to recovery mode, select a root terminal and type this:

```
less /var/log/messages
```

scroll down to the moment where the normal boot froze and let us know what is in there. Or post it here if you can.. BTW press q to leave the log.

---

### Post by Kid Charlemagne on 2010-04-27
It stops booting, but when I press control+alt+F1 it shows the following:

usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600

I wasn't sure if this would help, so I followed the second set of instructions. It ran through a bunch of stuff, but it stopped on the following:

Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/ init-bottom ...
Done.

I don't seem to be having any luck in recovery mode, but I think I can get the logs you want from the installed operating system. If I use the Live CD, it boots up, and then I can enter gksudo nautilus in the terminal. This brings up the root file browser window, and then I seem to be able to get any file or folder I want.

Just for future reference I put the installed OS home folder on a USB stick. It wouldn't let me drag and drop it, but it let me right click it, and send it as a zip drive. For some reason the folder on the USB stick is much larger than the original home folder. 

If I eventually reinstall the OS, and try to use that home folder, will I possibly be in the same position if the folder has corrupted files or folders?

---

### Post by P4man on 2010-04-28
So no error messages so far. But its not freezing either, since you can get to a TTY. I take it you tried running the xfix from the recovery menu?
Also, if you boot normally, and press control+al+f2, do you get a login prompt, and if so, can you log in?

Anyway, lets look at your log files. Can you attach Xorg.0.log, messages.log and kernel.log? Please first boot "normally" (the way it fails) so the log file reflects the correct situation its easy to spot the correct log entries.

> 
Just for future reference I put the installed OS home folder on a USB stick. It wouldn't let me drag and drop it, but it let me right click it, and send it as a zip drive. For some reason the folder on the USB stick is much larger than the original home folder.

Thats rather.. odd? Especially if you compressed the contents. Maybe you are not showing hidden/system files in nautilus and therefore getting the wrong size? Press control+h to show them.

anyway, I wouldnt do it the way you did, use the terminal :)

```
cp -r  /longpathtoyourhdd/home/yourusename /media/yourusbstick
```

Note that you can use TAB key to complete the path so you dont have to type it all and so you cant make typo's.
> 
If I eventually reinstall the OS, and try to use that home folder, will I possibly be in the same position if the folder has corrupted files or folders? 

Its not impossible, but I dont think so because currently you do not even get far enough to log in, so nothing in your home folder is actually used, hence the problem is elsewhere (system wide).

---

### Post by Kid Charlemagne on 2010-04-29
Not sure what a TTY is, and I definitely don't know how to run the xfix from the recovery mode.

I let the computer boot up, or try to and pressed control+alt+F2, but it didn't give me a login prompt - just a blank screen and a blinking cursor.

I'll try to get you the appropriate log files. It's kind of tough because I have to copy them from the netbook, walk them over to my desktop on a USB stick, and paste them into the message to you. I'm not sure, but I think I can only get those files when I access the installed OS using the Live CD. Is that okay?

---

### Post by P4man on 2010-04-30
> **Kid Charlemagne said:**
> Not sure what a TTY is, and I definitely don't know how to run the xfix from the recovery mode.
I meant a full screen terminal ("dos prompt")

as for xfix, I thought it was one of the options if you booted in to recovery mode. it might have a different name like "repair X configuration" or I dont know what. Been too long since I used 8.04

> I'll try to get you the appropriate log files. It's kind of tough because I have to copy them from the netbook, walk them over to my desktop on a USB stick, and paste them in the message to you. I'm not sure, but I think I can only get those files when I access the installed OS using the Live CD. Is that okay?

Yes thats fine. A live session wont overwrite the logs on your harddisk.

Frankly though.. ubuntu 10.04 has been released. Id suggest you download it, and put it on a usb stick and try it out. If it works well on your machine, install it and start using the computer again. Ubuntu 8.04 is reaching EOL status, so you will have to upgrade in a few months anyhow.

---

### Post by P4man on 2010-05-01
Kid Charlemagne,

I got the snippets from your log files, but you are showing much too little. There is nothing wrong in what you are showing me, but those only concern the very beginning of the boot, I need the last messages, when things go wrong.

Rather than using less /var/log/messages, use

```
tail /var/log/messages
```

and/or email me the complete messages log or the last (bottom) few screens of those log files

---

