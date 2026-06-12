---
title: "Windows XP fails to boot from boot selection screen"
date: 2009-07-06
forum: General Help
---

### Post by Rxk3r on 2009-07-06
Hello,

I am a new Linux user and so far am very impressed. I have a linux/xp dual boot configuration on my machine. When I select Windows XP pro from boot selection screen, a black screen that says  "starting up..." in the top left-hand corner comes up but XP never boots. I used the partition manager on the Ubuntu 9.04 live cd to set up the partition and install Ubuntu alongside XP. I have went through some forums and have not found a solution to the problem (maybe I have not looked enough).I have a 500 GB hard drive. Using gparted I can see that sda1 is the NTSF partition and is approximately 470 GB. Then there is another partition for Ubuntu which is sda2 (approx 30 GB) that is broken into sda5 and sda6. I noticed in gparted, there is no mount point listed for my hard drive until I actually open the hard drive to view its contents. Then gparted will list mount point as "/media/disk". I have posted the menu.lst file below to show how it currenty looks.. Thanks for any help as to why i can not get windows to boot. 



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
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
makeactive
chainloader    +1
savedefault

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
# kopt=root=UUID=75c3e73a-d848-4d7c-938d-57846400f28b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=75c3e73a-d848-4d7c-938d-57846400f28b

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        75c3e73a-d848-4d7c-938d-57846400f28b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=75c3e73a-d848-4d7c-938d-57846400f28b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        75c3e73a-d848-4d7c-938d-57846400f28b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=75c3e73a-d848-4d7c-938d-57846400f28b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        75c3e73a-d848-4d7c-938d-57846400f28b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75c3e73a-d848-4d7c-938d-57846400f28b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        75c3e73a-d848-4d7c-938d-57846400f28b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=75c3e73a-d848-4d7c-938d-57846400f28b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        75c3e73a-d848-4d7c-938d-57846400f28b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

---

### Post by lindsay7 on 2009-07-06
Type sudo fdisk -l (that is the letter l not the number 1) and post the results here that well show what is on your disk drive and we can go from there.

---

### Post by michy99 on 2009-07-06
I don't know if it makes a difference, but the windows entry is usually placed at the end, after the other entries.

Also, to keep certain character combinations from displaying as smilies on this forum, you can use the code box. Select text and click on the # at the top of the edit area. :)

---

### Post by lindsay7 on 2009-07-06
Michy 99 is correct this entry is in the wrong place. Delete (you and cut and paste) this from this grub file and paste it at the very end of the file. Do not make any more changes. You still need to give the out put of fdisk -l so that we can be sure of what is going on here but this needs to be fixed anyway.  Here is are the lines that need to be moved.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1
savedefault
```


Enter sudo gedit /boot/grub/menu.lst  in the terminal.   Make the changes save the file and reboot.

---

### Post by Rxk3r on 2009-07-06
Thanks for the quick replies everyone.. I will be at work for 3 hours then I will post the fdisk -l output as soon as i get home (5:30 central US time). 

Again,

Thanks.

---

### Post by lindsay7 on 2009-07-06
OK, good, fdisk will tell us for sure where your windows partition is and what is on the rest of your computer. It may be that the grub menu is correct  with it being on hd(0,0) and is so, making the change I gave you to your grub menu should fix it if your mbr is loaded and everything else is correct. Just post the fdisk result and go ahead and fix the grub menu anyway and let us know what goes on.. 

Check with you later.

---

### Post by Rxk3r on 2009-07-06
Ok so I opened a terminal and typed fdisk -l. Here is what it returned

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b637b63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       56784   456117448+   7  HPFS/NTFS
/dev/sda2           56785       60801    32266552+   5  Extended
/dev/sda5           56785       60630    30892963+  83  Linux
/dev/sda6           60631       60801     1373526   82  Linux swap / Solaris
```I also modified my menu.lst file as per request and rebooted. Did not make a difference. Only changed the boot screen order (putting windows back on bottom instead of at top of list).


I think this deserves mentioning.

I opened up rythmbox music player to listen to some tunes.. None of my songs were listed.. Then i realized that i had not clicked on the hard drive yet as there was no icon for it on my desktop so it was not mounted. That hard drive is the same hardrive XP is on. Is it possible that my hard drive is not mounting when it is suppose to. I am sure that it does not mount until i click on it (under places).

---

### Post by lindsay7 on 2009-07-06
It could be that your mbr for windows is bad or missing. Here is the info on how to repair it using your windows xp install disk.

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

Basically you start your computer with the windows disk in the cd drive and then go to the repair option and get to the command line. Enter fixmbr and press enter. This should reinstall the mbr to your drive. It will wipe or your grub menu and we will need to reinstall that, here are the commands to enter in the terminal using the Ubuntu live cd. 

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by Rxk3r on 2009-07-06
Thank you for your suggestion,

   I put my windows cd in the drive, restarted, booted from disk, could find no option to repair. It gives 3 options:
            1. install windows on this partition
            2. delete partition
            3. create a new partition.

Not sure how to get repair option up.. I will google it 

Thanks

---

### Post by lindsay7 on 2009-07-06
The instructions are in the web link that I gave you, you press r during the start up, etc,


[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by Rxk3r on 2009-07-06
Thanks for the link,

I found out that sometimes the system recovery is pre-installed on one's computer, as is my case. I do have an option for system recovery on the screen that allows you to change boot order, go into bios, etc. However, When I press the key to go into system recovery nothing happens. Its as if it just is not there. I think I am just going to forget about Windows until I need it for something. Beside this boot loader incident, I have not had any problems with Jaunty. I feel like since my partition with Windows on it isn't mounting on or right before boot that grub doesn't know Windows is there (if that is possible). Just for personal knowledge is there a way to make my partition 1 on HD mount prior to booting?

---

### Post by Rxk3r on 2009-07-07
I just wrote a different reply but Im not sure where it ended up so here I go again.

The link is helpful but I can't get into system recovery in order to run the commands. It turns out that some computers come pre-installed with the system recovery so one doesn't need the disk (that is my case). It is an option during start-up. However when I push the button to go into system recovery, nothing happens. Just like its not there. Not sure what that means. Maybe the system recovery got messed up during partitioning for Jaunty install. What is killing me about the whole deal is the fact that partition 1 (which is the partition that windows is on) doesn't mount until after I click on the HD under places. As if it were a removable disk or something. Maybe if I could get the HD to mount right before trying to boot windows off of it, Windows would be able to boot. I am not sure how it really works though so what do you think?

BTW, I think I am going to just give up Windows until I really need it for something.

Thank You,

Rxk3r
....Oh! now I see where that other reply went...

---

### Post by sububtu on 2009-07-07
Hiiii
im also a fresher ! working and exploring in ubuntu
i do hav the similar problem after removing ubuntu!
what i had done was 
booted with winxp cd reparing option frm the menu
ull get cmdprompt..
login using admin
type fixboot
but i dnt know that does the  ubuntu boot next time properly or not? 
if i was wrong sorry 4 wasting ur precious time....

im extremely new 2 ubntu, so im not familiar with ubuntu cmds and keywrds

---

### Post by Rxk3r on 2009-07-07
I am as well extremely new to linux.

 I put my windows xp disc in and booted from cd but I never get an option to repair, so I just tried to install windows in a different folder inside my other windows... :X. When I did that my linux grub loader was changed or something because then I couldn't load anything. When my computer started up it just said disk read error and would only let me restart, so I booted Ubuntu from cd and went into the terminal and setup the grub again. I can still get into Ubuntu but no Windows. As I mentioned in previous post, there is option to load system recovery on startup but thinking back, I remember at one time deleting a recovery partition on my computer and I am starting to think thats where the system recovery loads from. I wish I could find that friggin repair option, or reinstall it somehow without completely reinstalling everything.

If you have any revelations, feel free to post here as it would help me greatly..

Thank You,

Rxk3r

---

### Post by lindsay7 on 2009-07-07
You might find something here to help you.

//www.webtree.ca/windowsxp/repair_xp.htm

---

### Post by Rxk3r on 2009-07-07
Ahh..

Now I see why I can't get to system recovery.. I deleted my recovery partition a while back.. I can't really remember why and now I can't open system recovery. I will stick the disk in and see what happens. I tried it once already and was not given a system recovery option. Thank you very much for helping me out with this ongoing issue.

Thanks,

Rxk3r

---

### Post by Rxk3r on 2009-07-08
Ok so I reinstalled Windows and the Ubuntu so everything works now....sweet!!!

Rxk3r

---

