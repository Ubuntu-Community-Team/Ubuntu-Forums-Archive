---
title: "windows XP killed"
date: 2005-01-24
forum: General Help
---

### Post by dimvb on 2005-01-24
I installed ubuntu last night. After that windows seems to have died and doesn't load now when I choose it from the bootup loader. How should I get round this?

---

### Post by lockenkeyster on 2005-01-24
can you post the contents of /boot/grub/menu.lst ?

---

### Post by dimvb on 2005-01-24
Sure! But in a few hours, cause this happened to my home computer and I'll have to get home.

---

### Post by dimvb on 2005-01-24
the contents of the file requested
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,6)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by dimvb on 2005-01-24
the characters that the smiley has replaced are: 8)

---

### Post by dimvb on 2005-01-24
:))) are 8 and a bracket

---

### Post by Razvan on 2005-01-24
[QUOTE=dimvb]:))) are 8 and a bracket[/QUOTE]
 the "root" line under the "title Other operating systems:" seems funny to me, try getting rid of it

---

### Post by Olli on 2005-01-24
Please, do not follow the advice given in the prevíous message!  If the "root" is removed you will be in another trouble.

I have a similar menu.lst with the exception that I am directing the "default" to Title "Other Operating systems", this giving you time to choose the OS you want - In addition I have three operating systems to choose from, the third being SUSE 9.2 Pro. From my experience I do not believe that your MBR (Master Boot Record) is damaged.

---

### Post by lockenkeyster on 2005-01-25
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

_________________________---

I noticed that this is (hd0,0) and that linux is (hd0,6); I have had my windows partition not boot before when the second number was wrong. I'm guessing that this is the partition number (in order of creation), maybe try a different one (my default is (hd0,1)) ?

---

### Post by Olli on 2005-01-25
[QUOTE=lockenkeyster]title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

_________________________---

I noticed that this is (hd0,0) and that linux is (hd0,6); I have had my windows partition not boot before when the second number was wrong. I'm guessing that this is the partition number (in order of creation), maybe try a different one (my default is (hd0,1)) ?[/QUOTE]

(hd0,0) is just as it should be if the Windows XP is on the first IDE primary partition of the first hard disk (hda1). Please, read the man pages and/or info pages before giving erraneous advice!  As I wrote, I cannot see anything wrong in the menu.lst; if the windows partition does not open, there must be something wrong with the partition itself. What says fdisk /dev/hda ? (It happened me once, years ago, that I did not find which partition to install Mandrake on, with the result that it pushed Windows away and was installed on the first partition.) (hd0,6) means that Linux partition is on the second logical partition on the first hard disk. - I would be happy to hear whether you could resolve your problem.

---

### Post by Victor on 2005-01-25
I'm using Ubuntu for a month at this time, I'm enjoying it. But I can get my Windows XP to boot.
Exactly the same, I also tried by using fixmbr from the Xp install CD, but nothing improved it says Missing Operating System. I had to install grub on mbr again. I mounted my partitions and everything is Ok with my files, I dunno why I can get it to work. I saw there's a chance using fdisk /mbr but I'm starting to think it migth do the same that fixmbr, what do you think???

I've already changed the number  like hd0,3 it doesn't work.

---

### Post by Victor on 2005-01-25
I'm using Ubuntu for a month at this time, I'm enjoying it. But I can get my Windows XP to boot.
Exactly the same, I also tried by using fixmbr from the Xp install CD, but nothing improved it says Missing Operating System. I had to install grub on mbr again. I mounted my partitions and everything is Ok with my files, I dunno why I can get it to work. I saw there's a chance using fdisk /mbr but I'm starting to think it migth do the same that fixmbr, what do you think???

I've already changed the number  like hd0,3 it doesn't work.
that's what I get from fdisk /dev/hda:
The number of cylinders for this disk is set to 155127.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

I hope that aproaches us to a solution.

---

### Post by Olli on 2005-01-26
[QUOTE=Victor]I'm using Ubuntu for a month at this time, I'm enjoying it. But I can get my Windows XP to boot.
Exactly the same, I also tried by using fixmbr from the Xp install CD, but nothing improved it says Missing Operating System. I had to install grub on mbr again. I mounted my partitions and everything is Ok with my files, I dunno why I can get it to work. I saw there's a chance using fdisk /mbr but I'm starting to think it migth do the same that fixmbr, what do you think???

I've already changed the number  like hd0,3 it doesn't work.
that's what I get from fdisk /dev/hda:
The number of cylinders for this disk is set to 155127.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

I hope that aproaches us to a solution.[/QUOTE]

It doesn't. What is important that you do not try haphazardly silly things if you don't know what to do. 

I am sorry that I did not come to think that you don't know what fdisk does. So:

Key in /dev/hda
If you don't know what then look what stays on your display. There is 
Command (m for help)
key in m, and you'll see a table of commnands and actions.
Key in p  - print the partition table - and you should see something like

Device        boot  Start   End   Blocks    Id System
/dev/hda1    *      ....      ....      .....         7  HPFS/NTFS
/dev/hda2                                               f  W95/Ext'd
/dev/hda5                                               b W95/FAT32
/dev/hda6                                              83 Linux
/dev/hda7                                              82 Linux swap

This tells you that the first partition on the first IDE hard disk is WindowsNT4/2000/XP, and it is bootable. The second partition is extended partition that is divided in three logical partitions, the first (hd0,4) is FAT32 partition, the second (hd0,5) Linux partition, and the last one Linux swap partition.

Numbering of partitions in Grub menu.lst always begins from zero, therefore the first hd is hd0 etc. and the first partition is hd0,0.

I hope this helps both of you a step further. As I wrote before, I cannot find anything wrong in dimvb's menu.lst *provided* the Windows partition is /dev/hda1, and Linux /-partition is /dev/hda7.

---

### Post by Buffalo Soldier on 2005-01-26
Maybe this thread could be useful [http://ubuntuforums.org/showthread.php?t=8202&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=8202&page=1&pp=10)

---

### Post by lockenkeyster on 2005-01-26
[QUOTE=Olli](hd0,0) is just as it should be if the Windows XP is on the first IDE primary partition of the first hard disk (hda1). Please, read the man pages and/or info pages before giving erraneous advice!  As I wrote, I cannot see anything wrong in the menu.lst; if the windows partition does not open, there must be something wrong with the partition itself. What says fdisk /dev/hda ? (It happened me once, years ago, that I did not find which partition to install Mandrake on, with the result that it pushed Windows away and was installed on the first partition.) (hd0,6) means that Linux partition is on the second logical partition on the first hard disk. - I would be happy to hear whether you could resolve your problem.[/QUOTE]

I'm sorry that you find this advice erroneous, what I should have asked was whether they were sure that (hd0,0) WAS CORRECT. It is possible for there to be a utility partition in that space and for Windows XP to be in (hd0,1). (This is actually exactly what happened to me, which is why I asked - many computer sellers, such as Dell, put such a parition on the drive when it is shipped)

You're correct that nothing appears wrong, I was merely suggesting that he doublecheck the partition information.

---

### Post by Olli on 2005-01-27
[QUOTE=lockenkeyster]I'm sorry that you find this advice erroneous, what I should have asked was whether they were sure that (hd0,0) WAS CORRECT. It is possible for there to be a utility partition in that space and for Windows XP to be in (hd0,1). (This is actually exactly what happened to me, which is why I asked - many computer sellers, such as Dell, put such a parition on the drive when it is shipped)

You're correct that nothing appears wrong, I was merely suggesting that he doublecheck the partition information.[/QUOTE]

Now it is my turn to apologize. if I did hurt you. I should have emphasized the *if*. You may have noticed what I meant: before trying haphazardly different numbers in (hd0,x) one should ask the true partition system and advance only after it is known.

---

### Post by Victor on 2005-01-27
I'm sure anyone meant any harm on the comments. 
I thank everyone who is trying to help. I tried to change the number before but it's OK.
I got the repair diskette and used fdisk /mbr. Didn't work either. I'll check the link again and see if there's something I've missed. 
After I do that I'll let you know if I found anything, because It's been like a month since this all started.
Before I go check that once again I'll tell you what I did yesterday. used fdisk /mbr from a diskette made at Win98, i didn't work. It doesn't even show an error message. My PC stops there, just like when I try to start windows from the grub. No action at all. So I tried to make my Linux partition booteable, I had installed grub previously so if the mbr didn't run windows I could use grub from that partition, I  defined it as booteable and didn't work. So I had to install grub on the mbr again.
let me check what I missed and I'll be back.
Thanks

---

