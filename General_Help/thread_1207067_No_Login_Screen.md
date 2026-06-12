---
title: "No Login Screen"
date: 2009-07-07
forum: General Help
---

### Post by GO%)$@*1 on 2009-07-07
I'm having a bad bad problem (well not so bad compared to other ones I've had). My computer will boot, but it will not show the login screen. I have a Dell Inspiron E1505 running Ubuntu 9.04. Help please!
 
-kn

---

### Post by c0mput3r_n3rD on 2009-07-07
Is it just booting right to your desktop? What's happening?

---

### Post by GO%)$@*1 on 2009-07-07
It's booting, but there are multiple accounts so I have a login screen. Customized, too. The problem is, no login screen appears. It boots fine (save the fact that the usplash flickers then disappears)but then it goes to either a black screen or a screen with a few bars of color on both the top and the bottom. I have tried logging in from recovery mode, and no dice. I have restarted GDM as root from recovery mode too, and it doesn't work. The only solution I've found so far is that if I try Ubuntu from my 8.10 Live CD then I can access the filesystem, and with it the system files.

---

### Post by GO%)$@*1 on 2009-07-07
Some progress updates:

1. I've tried changing the drivers to vesa. No dice.

2. I've tried... 
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

...and still, you can probably guess what happened.

3. I tried booting without the usplash. I couldn't even find the option.

4. I've tried waiting. About an hour.

5. I am now looking through /var/log/dpkg.log. No idea how to find the target, though.

6. I've tried restarting GDM. Nothing, still.

ARGHHH!!!!

---

### Post by abhilashm86 on 2009-07-07
did you install any new themes?? better go to system->administrator->login window, maybe it'll get un-check for login window, check-mark and from next time, login window will appear.............

---

### Post by GO%)$@*1 on 2009-07-08
> **abhilashm86 said:**
> did you install any new themes?? better go to system->administrator->login window, maybe it'll get un-check for login window, check-mark and from next time, login window will appear.............
I wish it were that easy... I can't even access the desktop. After the usplash, all I get is either a black screen (the screen is on, it's kind of illuminated) or a screen with thin, colored bars on both the top and bottom of the screen. Do you know of any way you could check and/or change that option from root terminal (I can access it when I boot in safe mode-also, btw, I can't access the terminal using Ctrl+Alt+F1(2?))
After a lot of thinking, I think my computer is a locked up...

---

### Post by abhilashm86 on 2009-07-08
> **kuyanatan said:**
> I wish it were that easy... I can't even access the desktop. After the usplash, all I get is either a black screen (the screen is on, it's kind of illuminated) or a screen with thin, colored bars on both the top and bottom of the screen. Do you know of any way you could check and/or change that option from root terminal (I can access it when I boot in safe mode-also, btw, I can't access the terminal using Ctrl+Alt+F1(2?))
After a lot of thinking, I think my computer is a locked up...

if you messed up with bootsplash images, just when computer boots up, in the GRUB, press e for edit and go to kernel line and remove the bootsplash line at the ebd of line, like something ro splash.........
then press enter and b for boot, this will work, i've tried

after coming to normal GUI screen, open the file
```

 sudo gedit /boot/grub/menu.lst

```
and completely delete the bootsplash, it'll work fine,

this procedure you can also do using a live ubuntu cd.........

---

### Post by GO%)$@*1 on 2009-07-08
> **abhilashm86 said:**
> if you messed up with bootsplash images, just when computer boots up, in the GRUB, press e for edit and go to kernel line and remove the bootsplash line at the ebd of line, like something ro splash.........
then press enter and b for boot, this will work, i've tried

after coming to normal GUI screen, open the file
```

 sudo gedit /boot/grub/menu.lst

```
and completely delete the bootsplash, it'll work fine,

this procedure you can also do using a live ubuntu cd.........
Still no dice. Real daunting. Maybe I didn't delete a certain thing... i deleted only part. Can you tell me everything I was supposed to delete?

---

### Post by GO%)$@*1 on 2009-07-09
Anothrer update: even though the "ALT" terminal won't work, I can still use the magic SysRQ keys....

---

### Post by GO%)$@*1 on 2009-07-09
And another update: At the turning point, when the screen is either black or has the bars, I can see the "WiFi" status indicator lit up.

An example below, except for the fact that the light is actually lit up.
[http://www.notebookreview.com/assets/xps2/WiFiLight.JPG](http://www.notebookreview.com/assets/xps2/WiFiLight.JPG)

---

### Post by earthpigg on 2009-07-10
if you changed your menu.lst from the live cd, you may have changed the one on the live cd, and not on your hard drive. whoops!

if you are on the live cd:
```

ls /media/
```

to see what/where your hard drive is. you may have to mount it from the live cd by going to places -> computer -> find it on the left -> right click on it -> mount. and do 

```
cat /media/(hard drive here)/boot/grub/menu.lst
```

or, to edit it:

```
gedit /media/(hard drive here)/boot/grub/menu.lst
```

any time you are changing things on your computer from the live CD, you will have to do it that way.

---

### Post by GO%)$@*1 on 2009-07-10
> **earthpigg said:**
> if you changed your menu.lst from the live cd, you may have changed the one on the live cd, and not on your hard drive. whoops!

if you are on the live cd:
```

ls /media/
```

to see what/where your hard drive is. you may have to mount it from the live cd by going to places -> computer -> find it on the left -> right click on it -> mount. and do 

```
cat /media/(hard drive here)/boot/grub/menu.lst
```

or, to edit it:

```
gedit /media/(hard drive here)/boot/grub/menu.lst
```

any time you are changing things on your computer from the live CD, you will have to do it that way.
Thanks! Unfortunately, I have no idea *what *to change, if anything. I think I saw an option to upgrade my menu.lst or something like that when I was looking around in root terminal inside the recovery kernel. The first few times I tried ls /media/ it didn't do anything. After a  few more times, I got the result "disk". I followed the instructions you gave me. The thing is, like I said above, I have no idea what to change if I should be changing anything in the first place. Also, I didn't need to mount my hard drive. It was already mounted.

---

### Post by earthpigg on 2009-07-10
re-read about about the cat command.

use it to display your menu.lst. copy/paste the output here, so we can take a look.

---

### Post by GO%)$@*1 on 2009-07-10
> **earthpigg said:**
> re-read about about the cat command.

use it to display your menu.lst. copy/paste the output here, so we can take a look.
I will in my next post; I am on a different computer at the moment. I'm just posting to show a picture of my screen where the login screen is supposed to be. It's the one I get when I boot from recovery mode. It only shows part of the screen, a part of the top.

---

### Post by GO%)$@*1 on 2009-07-10
OK here's my menu.lst:
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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/Mac4Lin_GRUB3_v1.0.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password ----------
## password---------------------------------------
# password -----

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
# kopt=root=UUID=78707ef8-e8f0-433d-a4e7-3b73804b74b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78707ef8-e8f0-433d-a4e7-3b73804b74b7

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
uuid        78707ef8-e8f0-433d-a4e7-3b73804b74b7
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=78707ef8-e8f0-433d-a4e7-3b73804b74b7 ro quiet splash vga=792
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        78707ef8-e8f0-433d-a4e7-3b73804b74b7
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=78707ef8-e8f0-433d-a4e7-3b73804b74b7 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        78707ef8-e8f0-433d-a4e7-3b73804b74b7
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=78707ef8-e8f0-433d-a4e7-3b73804b74b7 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        78707ef8-e8f0-433d-a4e7-3b73804b74b7
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=78707ef8-e8f0-433d-a4e7-3b73804b74b7 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        78707ef8-e8f0-433d-a4e7-3b73804b74b7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by earthpigg on 2009-07-10
if someone ever tells you to 'comment / comment out' something or 'uncomment' it, they are talking about the #. if there is a # at the start of the line, that line will be ignored.

if you want to take notes in a config file for your own reference, put a # then whatever notes you want after it... that line will be completely ignored by anyone except someone with human eyes.

comment out hidden menu, color, and the _**splash image**_.

*crosses fingers*

if that fixes it, im sure you will be able to gander at the splash image file name and figure out where to point the finger :P

---

### Post by GO%)$@*1 on 2009-07-11
> **earthpigg said:**
> if someone ever tells you to 'comment / comment out' something or 'uncomment' it, they are talking about the #. if there is a # at the start of the line, that line will be ignored.

if you want to take notes in a config file for your own reference, put a # then whatever notes you want after it... that line will be completely ignored by anyone except someone with human eyes.

comment out hidden menu, color, and the _**splash image**_.

*crosses fingers*

if that fixes it, im sure you will be able to gander at the splash image file name and figure out where to point the finger :P
(Sigh...) Still no dice.

---

### Post by GO%)$@*1 on 2009-07-24
Hello? Is anyone there? Guess this is a stump...

---

### Post by GO%)$@*1 on 2009-07-27
Well I pretty much solved the problem. I reformatted and I'm near where I was before.  Thanks for your help everyone!

---

### Post by mainak_sen on 2009-07-27
Well, I am having pretty much the same problem. And I am in Hardy 8.04. I have been using Hardy 8.04 for more than a year now on this same machine, and this problem started only a couple of weeks back.

To re-iterate:

After the ubuntu boot-up splash-screen (and it echoes everything "OK") I get a blank screen (instead of the logon screen) following, sometimes, briefly, a blank screen with a single, dashed, color line near the top. Then it goes to the blank screen, sometimes with a cursor at the top-left. 
More interesting is that on a forced reboot, sometimes the problem is not there...sometimes there is the same problem. I dual boot XP and Hardy 8.04...what I have noticed is that after the problem occurs, if I force a reboot, and then thru Grub, boot XP first and then again restart and boot Hardy then I never get the problem. 

I have noticed a few other threads in the forum with similar problems...but with no definite solutions. May be some of the Forum Stuff or Ubuntu Gurus will help us with this and see if this is a recent bug introduced in one of the latest kernel updates.

Please help!


Thanks in advance!

---

### Post by RJ12 on 2009-07-27
Maybe the login screen is hidden have you tried entering your username/password when the login screen should be up?

---

### Post by GO%)$@*1 on 2009-07-29
Definitely weird...maybe it's something with the computer and not the system? Or a config file change? Even though I've solved the problem by reinstallation, I'd still like to know how to do this...

---

### Post by WAZZAT on 2009-08-01
That happened to me when I let unsupported? ALL? ATI video drivers and catalyst center install itself yesterday. Boots fine until desktop then 4 wide vertical bars and brolen top and bottom bars. Should have not taken the ATI plunge.

---

### Post by GO%)$@*1 on 2009-08-21
> **WAZZAT said:**
> That happened to me when I let unsupported? ALL? ATI video drivers and catalyst center install itself yesterday. Boots fine until desktop then 4 wide vertical bars and brolen top and bottom bars. Should have not taken the ATI plunge.
I've been looking around and I think it had something to do with the video card (or something like that). For some reason, before I had the problem, some driver was disabled and my visual effects were not working. I was playing around with Compiz before, so I guess that's what did it. Even though the problem has been solved for me (fresh install and format) I would still like to know what the problem *really* was and how to solve it in the future.

---

### Post by earthpigg on 2009-08-21
is your ATI video card supported?

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by GO%)$@*1 on 2009-08-21
I dunno. Couldn't find out. I *think* I had an ATI though...

---

