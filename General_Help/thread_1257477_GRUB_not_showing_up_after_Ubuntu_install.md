---
title: "GRUB not showing up after Ubuntu install"
date: 2009-09-03
forum: General Help
---

### Post by fredsmith456 on 2009-09-03
My GRUB boot loader is not showing up at startup. I just installed Ubuntu 9.04 Jaunty. I already have XP SP3 on my computer, and the computer boots directly into XP without showing GRUB. My problem is different from others because I did not install XP after Ubuntu. Isn't Ubuntu supposed to automatically install GRUB in the right place? By the way, here are my computer specs.

Processor: Pentium 4 3.0 Ghz
Ram: 1 Gb DDRII
Hard Drives: 500 Gb SCSI3 Drive for Data
                   120 Gb SCSI5 drive for the OS's

I partitioned 3 different partitions for Ubuntu on the 120 Gb drive.

1. 2 Gb Swap area
2. 10 Gb ext3 "/" partition for Ubuntu
3 15 Gb ext3 "/home" partition for data

How do I fix this problem?

Thanks, 
Fred

---

### Post by yabbadabbadont on 2009-09-03
Edit: nevermind.  I misread your post.  Sorry.

Edit2: OK, you probably are experiencing the same issue I have when installing Ubuntu on my machine.  Because it uses the generic libata driver for all disks now, the order of the drives gets swapped and it wants to install grub to the wrong drive.  I have to install in expert mode and when it gets to the grub installation, tell it none of the above (or something like that).  Then it will let you choose which drive the grub MBR will be installed upon.

---

### Post by blueridgedog on 2009-09-03
I would boot off of the LiveCD and re-install Grub using these commands:

In a terminal:
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.  If you think you bios is booting off of hd1, then you can use that instead.

Finally exit the grub shell
```

quit
```

If it works, we may need to go back and add an entry for XP.

---

### Post by fredsmith456 on 2009-09-04
Thanks for the quitck reply, both of you.

@Yabba:
How do you install in "expert mode"? I haven't seen that function on the installer.

@blueridge:
I've tried that set of commands. Doesn't help.

---

### Post by yabbadabbadont on 2009-09-04
When you are at the boot menu when the CD first loads, hit F6 to toggle expert mode.  However, it may be that it is only an option when using the alternate installation CD...  (which is all I ever use)

---

### Post by akakingess on 2009-09-04
> **fredsmith456 said:**
> Thanks for the quitck reply, both of you.
@blueridge:
I've tried that set of commands. Doesn't help.

You did try this after booting off of the live CD, correct? I don't mean to be condescending, just want to make sure we aren't missing something basic. And if so, at which point did it fail, or did all of the commands run and acted like they worked and then GRUB didn't show up upon reboot?

---

### Post by blueridgedog on 2009-09-04
> **fredsmith456 said:**
> 
@blueridge:
I've tried that set of commands. Doesn't help.

Where did it find the boot files?

Where did you install grub to?  Did you try the other drive as well?

---

### Post by fredsmith456 on 2009-09-04
@Yabba: I'll try that.

EDIT: I can't find the "Expert Mode" function. The options under F6 are:

acpi=off
noapic
nolapic
edd=on
Free software only

@akakingess: I did try this after booting off the live CD. Um, I'll run the commands again and copy and show the result here.

EDIT: Here is what my terminal screen looked like right before the quit command:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 


@BlueRidge: It found the boot files at hd(1,2). No, I didn't try the other drive.

---

### Post by blueridgedog on 2009-09-04
You typed:

```
grub> setup (hd1,2)
```

It should be:

```
setup (hd0) 
```

In order for grub to be installed in the mbr of the first hard drive, or 

```
grub> setup (hd1)
```

for it to be installed in the mbr of the second hard drive.

Try hd0.

---

### Post by fredsmith456 on 2009-09-04
@BlueRidge: Thanks, I'll try that. I'll report back in the below space afterwards.

EDIT: This is the result in the terminal before the quit command. I'll report in a new post once I reboot.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by blueridgedog on 2009-09-04
Note you still need the root part...everything else stays the same.

---

### Post by fredsmith456 on 2009-09-07
Okay, GRUB showing up at startup now. This reply is made on my new Ubuntu install! Thanks, everyone. I may post more here if I find more problems.

EDIT: Okay, everything is NOT fine. Now GRUB shows up and I can boot into Ubuntu, but I can`t boot into Windows anymore. It says Error 12 Invalid Device. I looked at this:
[http://ubuntuforums.org/archive/index.php/t-464695.html](http://ubuntuforums.org/archive/index.php/t-464695.html)
archive thread, and I am now trying to fixmbr and fixboot. Any suggestions to get both OSes working?

EDIT2: I forgot to add, there`s a problem with the sudo command in terminal also. Everytime I try to use it, it asks for a password. However, (here`s the problem) I can`t type anything into that field, meaning I can`t type the password, meaning I can`t do anything with sudo. Any fixes?

---

### Post by blueridgedog on 2009-09-08
> **fredsmith456 said:**
> 
EDIT: Okay, everything is NOT fine. Now GRUB shows up and I can boot into Ubuntu, but I can`t boot into Windows anymore. It says Error 12 Invalid Device.

EDIT2: I forgot to add, there`s a problem with the sudo command in terminal also. Everytime I try to use it, it asks for a password. However, (here`s the problem) I can`t type anything into that field

For 1, can you post the contents of /boot/grub/menu.lst?

You can access it with:

```
gedit /boot/grub/menu.lst
```

For 2, note that nothing appears when you type the password for an su, this is normal.  what happens when you type the password and hit enter?

---

### Post by fredsmith456 on 2009-09-13
This is the contents of my installed menu.lst.


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
default        3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=c3bd4446-4738-49f8-bfe3-e1b54537fb08 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c3bd4446-4738-49f8-bfe3-e1b54537fb08

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
# defoptions=quiet splash vga=769

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
uuid        c3bd4446-4738-49f8-bfe3-e1b54537fb08
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c3bd4446-4738-49f8-bfe3-e1b54537fb08 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        c3bd4446-4738-49f8-bfe3-e1b54537fb08
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c3bd4446-4738-49f8-bfe3-e1b54537fb08 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        c3bd4446-4738-49f8-bfe3-e1b54537fb08
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c3bd4446-4738-49f8-bfe3-e1b54537fb08 ro quiet splash vga=769 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c3bd4446-4738-49f8-bfe3-e1b54537fb08
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c3bd4446-4738-49f8-bfe3-e1b54537fb08 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c3bd4446-4738-49f8-bfe3-e1b54537fb08
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


I can't tell if sudo works now, because I'm in a live session.

---

### Post by louieb on 2009-09-13
> **fredsmith456 said:**
> ```


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```
IF thats the code you used to get the grub menu to display  then it means windows is on the 1st drive and the entry now looks for it on the 2nd drive

```
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```you windows entry should look like this.

```
title        Microsoft Windows XP Professional
 rootnoverify    (hd0,0)
 makeactive
 chainloader    +1
```

> Isn't Ubuntu supposed to automatically install GRUB in the right place? By the way, here are my computer specs.

Naw its just an educated guess: from the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")
> there are several ways in which your computer can become unbootable. For example, most operating systems don't tell GRUB how to map BIOS drives to OS devices correctly—GRUB merely guesses the mapping. This will succeed in most cases, but not always.

---

### Post by fredsmith456 on 2009-09-16
Although I haven't tried it, as far as I understand, the only real difference is the 
 rootnoverify    (hd1,0)
being 
 rootnoverify    (hd0,0)
The other parts, such as 
savedefault
(makes WinXP the default OS, I think) and 
map        (hd0) (hd1)
map        (hd1) (hd0)
(makes the hard drives switch) are completely harmless.

---

### Post by louieb on 2009-09-17
Don't know how harmless the map commands are when windows is on the 1st drive. May prevent it from booting - may not. 

I do know that when windows is on the 2nd drive -  in order for Grub to boot windows - I have to include them.

---

### Post by fredsmith456 on 2009-09-23
So, All I have to do is use your suggestion, but keep the "makedefault".

---

### Post by Darkwing-Duck on 2009-09-24
Here is a good guide to restoring GRUB and fixing your MBR.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

### Post by fredsmith456 on 2009-09-27
Thanks for all your help, people!

I just deleted the "map" commands, and "rootnoverify (0,0)". 
Then I repeated the GRUB commands from earlier.
Done!

---

