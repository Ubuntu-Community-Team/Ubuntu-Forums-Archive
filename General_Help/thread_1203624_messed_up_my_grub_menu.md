---
title: "messed up my grub menu"
date: 2009-07-03
forum: General Help
---

### Post by Zoyberk on 2009-07-03
few minutes ago i just did horible stupidity XD
I messed up my grub menu :p

i used this guide [http://kubuntuforums.net/forums/index.php?topic=3096505.new;topicseen#new]("http://kubuntuforums.net/forums/index.php?topic=3096505.new;topicseen#new")
I did all it said to did except 
> installed with:
Code:
```
sudo dpkg -i grub-gfxboot_0.97-11_i386.deb
```
i just clicked on deb package and installed it.

when i rebooted i stuck at something like terminal or whatever it is XD
and I-m dual booting vista and kubuntu 9.04, and currently i1m running kubuntu live cd if that is mybe important.

I`d be really glad if somebody could tell me how to fix that, and mybe how to install that graphic boot thing :p

---

### Post by lindsay7 on 2009-07-03
Type these commands in the terminal,

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


Thanks to Presence1960 for the write up

---

### Post by Zoyberk on 2009-07-04
did all you said,  when i rebooted i get somethink like

GRUB stage loaded 1.5
GRUB loading
error 2

or somethink like that.
when i first did it i think i acedently wrote setup (hd0) insted of setup (hd0,4) 

then i did all from begining agem, but still same error.
What should i do now :)

---

### Post by blueridgedog on 2009-07-04
While booted on a LiveCD, can you mount your linux hard drive partition (/media/disk for example) and post the output of the following commands?

```
ls /media/disk/boot
```

and
```

sudo cat /media/disk/boot/grub/menu.lst
```

and

```
sudo fdisk -l
```

If your drive mounts to another location change /media/disk as needed or if you need help mounting it to a specific location or determining where it is mounted, post back.

---

### Post by Cloggsy on 2009-07-04
While I'm not a code wizard like the others in this thread, once you are back up and running "that graphic boot thing" is KGRUBEditor. It's downloadable from the normal repositories and also works under Ubuntu as well as Kubuntu.

---

### Post by Zoyberk on 2009-07-04
> **blueridgedog said:**
> While booted on a LiveCD, can you mount your linux hard drive partition (/media/disk for example) and post the output of the following commands?....

Here it is

first one
```
ubuntu@ubuntu:~$ ls /media/disk/boot
abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-13-generic         System.map-2.6.28-11-generic
config-2.6.28-11-generic      System.map-2.6.28-13-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-11-generic
grub                          vmcoreinfo-2.6.28-13-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
ubuntu@ubuntu:~$

```

second one
```
ubuntu@ubuntu:~$ sudo cat /media/disk/boot/grub/menu.lst  
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
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         10                                                             

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a55bb32b-5768-475d-80c0-a343f5f7a002 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=a55bb32b-5768-475d-80c0-a343f5f7a002

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

title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            a55bb32b-5768-475d-80c0-a343f5f7a002 
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=a55bb32b-5768-475d-80c0-a343f5f7a002 ro quiet splash                                                  
initrd          /boot/initrd.img-2.6.28-13-generic                              
quiet                                                                           

title           Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid            a55bb32b-5768-475d-80c0-a343f5f7a002                 
kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=a55bb32b-5768-475d-80c0-a343f5f7a002 ro  single                                                       
initrd          /boot/initrd.img-2.6.28-13-generic                              

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            a55bb32b-5768-475d-80c0-a343f5f7a002
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=a55bb32b-5768-475d-80c0-a343f5f7a002 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            a55bb32b-5768-475d-80c0-a343f5f7a002
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=a55bb32b-5768-475d-80c0-a343f5f7a002 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            a55bb32b-5768-475d-80c0-a343f5f7a002
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:~$

```

third one
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x943c943c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8318    66809856    7  HPFS/NTFS
/dev/sda2            8319       38913   245754337+   5  Extended
/dev/sda5            8319       37878   237440668+  83  Linux
/dev/sda6           37879       38913     8313606   82  Linux swap / Solaris
ubuntu@ubuntu:~$

```
thats it 


and thanks for that info Cloggsy XD

---

### Post by blueridgedog on 2009-07-04
Well, your boot files and your menu.lst looks normal.  

You can try and re-install grub:

Bootup a live cd, open a terminal and do the following.
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

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

Reboot the system and if things aren't back to normal then I don't think it is a grub issue.

---

### Post by Zoyberk on 2009-07-04
did as you said. Still same error.

Is it mybe wrong cuz i copied some fille in boot file in my disc and i alo added line in menu.lst or whatever is it.
I tried to remove it, but dunno how to run nautilus in live cd mdoe so i will be able to edit kubuntu partition.

---

### Post by blueridgedog on 2009-07-04
> **Zoyberk said:**
> did as you said. Still same error.

Is it mybe wrong cuz i copied some fille in boot file in my disc and i alo added line in menu.lst or whatever is it.
I tried to remove it, but dunno how to run nautilus in live cd mdoe so i will be able to edit kubuntu partition.

Tell me more then about what specifically happens when you boot.  

Do you get the menu?

Can you boot into your vista partition?

What happens when you try and boot one of your Ubuntu entries?

---

### Post by Zoyberk on 2009-07-05
when i try what you said me i get exactly

Grub Loading Stage 1.5

Grub Loading Please Wait...

Error 2

before i did what you told me i got somethink diffrent, somethink like terminal, if i clicked tab i could see posibile comands...

i googled that error litle and i found out that lot ppl alreeady had problem whit this, so i gonna try some solutions from google XD

---

### Post by Zoyberk on 2009-07-05
> **blueridgedog said:**
> Tell me more then about what specifically happens when you boot.  

Do you get the menu?

Can you boot into your vista partition?

What happens when you try and boot one of your Ubuntu entries?


....i dont get menu, i just get somethink asus....where i can pres f2 to enter bios, and then i got that grub error 2

---

### Post by blueridgedog on 2009-07-05
The only things that can go wrong doing the re-install of grub are either you issue an incorrect root hd?,? statement (telling it your root is hd0,1, when it is really hd0,0) and setting up the wrong hard drive with the setup hd? command (setting up hd0 when your system is really booting off of another drive).  Do you remember what values you used? 

Based on your earlier posts, you only have one hard drive, so "setup hd0" would be right, but since your Linux boot partition is on the fifth portion of your hard drive (first logical partition), you  may have used an incorrect root command.  It should be "root hd0,4".

---

### Post by Zoyberk on 2009-07-05
i tried diong that like 10 times, i used 1,4 0,4 and some other combinations, at last one too

neverming...after serchng google half a day just got pissed and decided to format kubuntu partition(had only like 3GB data to backub) now its at 52%, hope it will work then XD

---

