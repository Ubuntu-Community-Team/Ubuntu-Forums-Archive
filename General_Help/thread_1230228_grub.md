---
title: "grub"
date: 2009-08-03
forum: General Help
---

### Post by davewickett on 2009-08-03
ok ive come across a bit of a problem i done a fresh install & done use all the disc everything looked fine but when i booted up i get a msg loading grub error 21 so i tryed to install linux mint daul-boot to put the bootloader on it but still have the same msg how can i get grub to show up please i really need this on im running of the live cd at the moment thanks

---

### Post by 73ckn797 on 2009-08-03
Open Applications/Accessories/Terminal and run this command:

```
sudo fdisk -l
``` that is a lower case L not 1. Post that info.

Also when in terminal enter:
```
gksudo gedit /boot/grub/menu.lst
``` and post the last section where the operating systems are shown for boot order. We can work from that info to help.

You could just open "Computer" and go to the directory in the last command and open the "menu.lst" in a text editor. That way you cannot edit by accident.

Copy and past the first command results to your next post. Use ctrl-alt-c when in terminal to copy the info.

---

### Post by davewickett on 2009-08-03
> **73ckn797 said:**
> Open Applications/Accessories/Terminal and run this command:

```
sudo fdisk -l
``` that is a lower case L not 1. Post that info.

Also when in terminal enter:
```
gksudo gedit /boot/grub/menu.lst
``` and post the last section where the operating systems are shown for boot order. We can work from that info to help.

You could just open "Computer" and go to the directory in the last command and open the "menu.lst" in a text editor. That way you cannot edit by accident.

Copy and past the first command results to your next post. Use ctrl-alt-c when in terminal to copy the info.



thanks alot mate for getting back to me anyway here is output for 1st 1


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8499e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29272   235127308+  83  Linux
/dev/sda2           29273       30401     9068692+   5  Extended
/dev/sda5           29273       30401     9068661   82  Linux swap / Solaris


the next 1 opens up a blank page i did have it the last time i booted of live cd but cannot remember what i put to get it and yes i got a list of all my boot order

---

### Post by nothingspecial on 2009-08-03
Ignore this see below

---

### Post by nothingspecial on 2009-08-03
I`ve just noticed you are running off the live cd.

In that case you need to mount your ubuntu partition to read the menu.lst.```


sudo mkdir /ubuntu
```
```
sudo mount -t ext3 /dev/sda1 /ubuntu
```

```
cat /ubuntu/boot/grub/menu.lst
```

---

### Post by davewickett on 2009-08-03
when i do that i get this                          a box with this in 
; height: 34px; text-align: left;">cat /ubuntu/boot/grub/menu.lst</pre>

---

### Post by nikhilk on 2009-08-03
> **davewickett said:**
> when i do that i get this                          a box with this in 
; height: 34px; text-align: left;">cat /ubuntu/boot/grub/menu.lst</pre>

That does not make much sense. So to clear the confusion, did the mount command run OK? Did the "cat" command give some error?

---

### Post by nothingspecial on 2009-08-03
I`ve never seen that before?????

The mkdir command and mount command should be issued seperately. My fault, shouldn`t have put them in the same code tags. Perhaps that`s what happened.

---

### Post by davewickett on 2009-08-03
ok got it sorted so i hope this can help me now then 


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
timeout        3

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
# kopt=root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82ca3ff1-aab1-4bef-97bf-0d5d93873100

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
root@ubuntu:/home/ubuntu#

---

### Post by nikhilk on 2009-08-03
Could you provide the output of this command?
```
sudo blkid /dev/sda1
```

---

### Post by davewickett on 2009-08-03
root@ubuntu:/home/ubuntu# sudo blkid /dev/sda1
/dev/sda1: UUID="82ca3ff1-aab1-4bef-97bf-0d5d93873100" TYPE="ext3"

---

### Post by nikhilk on 2009-08-03
> **davewickett said:**
> root@ubuntu:/home/ubuntu# sudo blkid /dev/sda1
/dev/sda1: UUID="82ca3ff1-aab1-4bef-97bf-0d5d93873100" TYPE="ext3"

Looks OK. I was just checking if the correct entry was present in the fstab.
I am running out of ideas here everything looks to be OK.

---

### Post by martinbaselier on 2009-08-03
grub needs to have the correct partition info. If you changed partitions after grub is installed it won't run. I've had similar problems in the past. 

You need one of these commands:

sudo grub-install /dev/sda1

or

sudo grub-install /dev/sda

One will give you an error, the other one works.

---

### Post by merlinus on 2009-08-03
You might try this:

Boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

Remove the cd and restart.

---

### Post by davewickett on 2009-08-03
> **merlinus said:**
> You might try this:

Boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```Remove the cd and restart.



just tryed this & still not booting everything was saying ok to it all as it went down but just did not boot and still getting same errror do you have anything else i could try as i know this must be something silly as its saying everything is installed fine really need to fix this now do you need me to post what it said when i put your commands in thanks for all your help

---

### Post by davewickett on 2009-08-03
> **martinbaselier said:**
> grub needs to have the correct partition info. If you changed partitions after grub is installed it won't run. I've had similar problems in the past. 

You need one of these commands:

sudo grub-install /dev/sda1

or

sudo grub-install /dev/sda

One will give you an error, the other one works.



ok just tryed your commands & got this 

buntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

there must be something i can do to get this to work

---

### Post by nothingspecial on 2009-08-03
I haven`t got time to help right now but to help yourself have a look [[COLOR="Magenta"]here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems")

---

### Post by davewickett on 2009-08-03
ok mate ill try on my own but someone on here might know how i could fix this problem so like i said thank you anyway

---

### Post by merlinus on 2009-08-03
First of all, change this in menu.lst

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

to this

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

In other words, place a hashmark (#) in front of hiddenmenu so at least grub shows up on your screen.

Next, post the messages from the grub commands I gave, especially what came up after entering 

```
find /boot/grub/stage1
```

---

### Post by davewickett on 2009-08-03
ok im just trying something first then when ive rebooted ill give your 1 a go and let you know mate

---

### Post by davewickett on 2009-08-03
> **merlinus said:**
> First of all, change this in menu.lst

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

to this

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

In other words, place a hashmark (#) in front of hiddenmenu so at least grub shows up on your screen.



Next, post the messages from the grub commands I gave, especially what came up after entering 

```
find /boot/grub/stage1
```



ok the only way i can get the menu lst up to config is in the terminal with
sudo mkdir /ubuntu      Code:
     sudo mount -t ext3 /dev/sda1 /ubuntu 
     Code:
     cat /ubuntu/boot/grub/menu.lst 
them commands i got gave so how do i edit them




find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory

---

### Post by merlinus on 2009-08-03
After mounting your ubuntu partition, then

```
gksudo gedit /ubuntu/boot/grub/menu.lst
```

to edit, and then post contents.

---

### Post by davewickett on 2009-08-03
ok done that here it is 


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
timeout        3

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
# kopt=root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82ca3ff1-aab1-4bef-97bf-0d5d93873100

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=82ca3ff1-aab1-4bef-97bf-0d5d93873100 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        82ca3ff1-aab1-4bef-97bf-0d5d93873100
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-08-03
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu

[COLOR=Black]Place a hashmark (#) in front of the line in red, or you will have to press Esc superfast in order to see the grub menu.

Then enter these commands in a terminal and post any messages:

[/COLOR][/COLOR]```
sudo grub
root (hd0,0)
setup (hd0)
quit
```[COLOR=Red][COLOR=Black]
and restart.

To be clear, 0 is the number zero and not the letter O.
[/COLOR] [/COLOR]

---

### Post by davewickett on 2009-08-03
done what you said 

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

thats what i got to let you know and did that in the config file and saved it about to reboot now ive go my fingers crossed let you know in a min

---

### Post by davewickett on 2009-08-05
ok i installed ubuntu to the hole drive & was getting error 21 grub not loading so i had to install vista then install ubuntu & i want i want to know if i can get rid of vista & put a other linux on where vista was but keep them both in 1 boot loader 
[ATTACH]123774[/ATTACH] this is what it looks like now

---

### Post by merlinus on 2009-08-05
Yes.  You can gparted to format the existing vista partition as ext3, install another linux os, and it should automatically add itself to grub.

If not, you can do it manually.

---

### Post by davewickett on 2009-08-06
could i just install a other os linux like linux mint or fedora from disc & when i get to partitions just put it on where vista is & make a swap partition aswell, will it show up on the grub then aswell, i would like backtrack where windows is (sda1) i have bt4 betta on iso how would i put that on where sda1 is the best way 

ps. why when i installed ubuntu to the whole disc it would not boot msg saying error 27 grub not loading 

thanks for all your help as useual 

dave
[ATTACH]123819[/ATTACH]

pps when i get to the part add grub where do i put it when it says sd0.0 sda1 do i put it on the main hd
this is what i have now

sda1=      84.7gb       (vista)
sda5 =      142.26gb      (ubuntu)
linux swap=     7.19gb       (ubuntu swap file)
sda2   =   9.34gb           (hp recovery)
unallocated = 2.26mb
unallocated =6.13mb 		 		  		  		 		  		  		  		  		 			 			 				[IMG]http://forums.remote-exploit.org/images/backtrack4/misc/progress.gif[/IMG] []("http://forums.remote-exploit.org/editpost.php?do=editpost&p=146092")

---

### Post by merlinus on 2009-08-06
You can use the ame swap partition for all linux installations.  In general, installing will give you the option of which partition to use, so select sda1.

And I would let grub install itself to hd0, or hd0,0.

I don't know why you got the error after choosing use entire disk when installing ubuntu, but did we not fix that problem?

---

### Post by davewickett on 2009-08-07
please help ive installed linux mint where sda1 was (vista) & now i can not boot again getting msg error 21 grub loading ive tryed adding bootloader to what you said and to the main drive but just getting same msg each time its saying they are installed ok what can i do to get them to boot of a bootloader  again please help this is all i need thanks
[ATTACH]123987[/ATTACH]

---

