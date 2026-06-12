---
title: "Unable to boot into Vista after installing Wubi"
date: 2009-09-15
forum: General Help
---

### Post by visual_decoy on 2009-09-15
Hello forum 

I have encountered a problem after installing Wubi. I am dual booting Vista and Ubuntu 8.10 on a Thinkpad t400. 

Today I decided to install 9.04 on my Vista partition using Wubi. I used the 9.04 live cd to do this. No problems were encountered during installation as far as I can tell. 

Since the install, I have been unable to boot into Vista. After the boot screen with the green microsoft scroll bar, I encounter the black screen of death. This is a blank black screen with only the mouse cursor displayed. ctrl+alt+del does not work. The computer hangs on this screen forever without progressing to the login screen. The same happens if I try to boot into safe mode. I am able to boot into the laptop's recovery partition and run system recovery/restore etc, but the problem persists. 

The freshly installed 9.04 works fine. 

My old 8.10 on a separate partition is unaffected. However, when I try to mount my Vista partition, I get the following message: 

"Unable to mount the volume 'vista'. $LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sda2': Operation not supported Mount is denied because NTFS is marked to be in use." 

I have googled this problem and there appear to be many causes of the black screen of death. But my particular problem only occurred after installing Wubi, which is why I'm posting it here. Any advice will be greatly appreciated!

---

### Post by rocket16 on 2009-09-15
Did you try Repairing Vista from the DVD?

---

### Post by P4man on 2009-09-15
I suspect it may have something to do with the recovery partition and grub's partition numbering.  Can you post the contents of your menu.lst and the output of "sudo fdisk -l" ?

---

### Post by visual_decoy on 2009-09-15
@ rocket16

I did not receive one with the laptop. And I stupidly did not create burn one from the recovery partition when i first bought the laptop :oops:

---

### Post by visual_decoy on 2009-09-15
menu.lst

```
# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=66c05f11-31ee-4443-987a-cf3e0f459690 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66c05f11-31ee-4443-987a-cf3e0f459690

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

title        Ubuntu 8.10, kernel 2.6.27-14-generic
uuid        66c05f11-31ee-4443-987a-cf3e0f459690
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=66c05f11-31ee-4443-987a-cf3e0f459690 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid        66c05f11-31ee-4443-987a-cf3e0f459690
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=66c05f11-31ee-4443-987a-cf3e0f459690 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        66c05f11-31ee-4443-987a-cf3e0f459690
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=66c05f11-31ee-4443-987a-cf3e0f459690 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        66c05f11-31ee-4443-987a-cf3e0f459690
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=66c05f11-31ee-4443-987a-cf3e0f459690 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        66c05f11-31ee-4443-987a-cf3e0f459690
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```output of sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f6eac6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       10137    79885132+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10138       19457    74859120    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           10138       11388    10039648+  83  Linux
/dev/sda6           19072       19457     3099568+  82  Linux swap / Solaris
/dev/sda7           11388       19072    61719808+  83  Linux

Partition table entries are not in disk order

```

---

### Post by P4man on 2009-09-15
Please use ```
 tags to keep post length reasonable :)

I notice you're still using ubuntu 8.10. I do seem to recall it struggled with recovery partitions. Ubuntu 9.04 should handle them gracefully, and make boot entries for both vista and the vista recovery partition.

I guess there a few things you can do:

- You could burn a ubuntu 9.04 livecd, and boot from there, and "repair" grub with that. 

-You can wait until a grub guru tells you exactly what to do :)

-you can try something Im not sure will work :p OPen a terminal and type

[CODE]gksudo gedit /boot/grub/menu.lst
```

replace this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1 
```

with this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1 

title Windows Vista P4man's guess
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1 
```

---

### Post by rocket16 on 2009-09-15
If that too does not work, then the thing is that, your LogonUI.exe has encounted a problem or potential virus-infection. So, try to find the file from the Vista CD (load it in Ubuntu) and replace the System32/logonUI.exe with the file (You may also get it on the Internet).

---

### Post by rocket16 on 2009-09-15
Download the LogonUI from [http://fc04.deviantart.com/fs22/f/2007/347/f/7/Windows_Vista_Default_Login_9_by_RaulWindows.zip](http://fc04.deviantart.com/fs22/f/2007/347/f/7/Windows_Vista_Default_Login_9_by_RaulWindows.zip)
Next go to en-US folder, and open the folder macthing your Veriosn (i.e various logon screens are there, Home-Premium, Ultimate etc.) Now, replace the file.

---

### Post by rocket16 on 2009-09-15
And don't feel embarassed my friend. We all make mistakes in our life.

---

### Post by visual_decoy on 2009-09-15
@ p4man 

May I ask why you think the error involves grub? My understanding of grub is that it lets you choose which OS to load during startup. However in my case, I don't think the problem is one of *choosing* to boot Vista, but rather the completion of that boot process (the black screen comes *after* the screen with the green scroll bar, which I thought indicates that Windows is loading). I hope that makes sense. 

@ rocket 16

That all sounds reasonable. But how can I copy and paste the file if I can't boot into windows or safe mode or mount the partition through ubuntu? 

Also, why do you think wubi has messed with the Vista login screen exe (of all things)? Surely this is not a normal thing to occur? 

Thanks fellers I appreciate the help.

---

### Post by ram2500 on 2009-09-15
Well, you got past the splash screen...good sign. 
It's also a good sign you see a mouse cursor. I assume that you didn't have any error messages such as "such-and-such file is missing". So, it does go through the motions of booting, but hangs. 

By black screen of death, do you mean that it's running CHKDSK? Installing Wubi might prompt Windows to run Chkdsk on boot. 

I agree with the previous posters...I'm sure that the logon file(s) have been corrupted, moved or deleted (but why wouldn't it say something about it being [missing, corrupted, moved]?)...that's puzzling.

If it's not an inconvenience, start in Safe Mode and let it alone for awhile...if, say after several minutes, there's no login screen, then we have a problem. 

If you have made a separate partition for Ubuntu, you may be able to copy the necessary files to the Windows partition. You can read and write to NTFS volumes from within Ubuntu IF and ONLY IF you have Ubuntu and Windows on separate partitions (not just as a file from within Windows, the default for Wubi installs).

---

### Post by visual_decoy on 2009-09-15
> I assume that you didn't have any error messages such as "such-and-such file is missing". So, it does go through the motions of booting, but hangs. 

yes

>  By black screen of death, do you mean that it's running CHKDSK? 

I don't know what this means

> If it's not an inconvenience, start in Safe Mode and let it alone for awhile...if, say after several minutes, there's no login screen, then we have a problem. 

I'm doing that now (and I'm pretty sure i've let it just sit there for a while yesterday). doesn't appear to do much. The hard disk LED on the bezel occasionally flickers. that's about all. 

> If you have made a separate partition for Ubuntu...

I do. But I can't mount it. See my original post. :(

---

### Post by wilee-nilee on 2009-09-15
So on a wubi install it first copies the iso to a file and the reboot installs it very similar to a standard windows or even linux install, except that linux doesn't need to save the iso. You might check the windows boot-loader if the problem is not a coruption, here are 2 good instructions to the boot-loader stuff. Also a super grub disc should get you into a regular vista setup to edit.  [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)  

[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

You also might considor just running jaunty in a virtual in hardy.

---

