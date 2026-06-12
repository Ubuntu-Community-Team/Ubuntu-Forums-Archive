---
title: "Forgot Password...Help!"
date: 2009-06-25
forum: General Help
---

### Post by Xeginy on 2009-06-25
Okay, I'll bite...I did not forget the administrative password, I never knew it in the first place.  I got this computer from my brother, right before he left for med school.  He got it from somebody else, and he never even turned it on.  He wasn't interested in a computer with a Linux OS.  So, anyway, I don't need a password to turn it on (thankfully) but I do need one to install updates, install any new software, etc.  I got a lot of great tips on how to change it, but they all involve one thing: the grub prompt.  Now, I don't know lot about Linux (I'm a new user) but as far as I can tell, when my computer turns on, there IS no grub prompt.  I can press "esc" or type "pretty pony princess" and no grub prompt will appear.  I even found some directions that had screenshots (very helpful) and my startup does not look like that.  So what's the deal?  Is there any way to change the password without using the grub prompt?

In case this helps, I'm running Ubuntu 8.1.

And by the way, if there is a thread exactly like this, don't hesitate to point me to it.  There were just 1000+ pages of threads, so...yeah.  Can't exactly look through all those.  Any help at all will be muchly appreciated.

---

### Post by cmost on 2009-06-25
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Or, my recommendation would be to install a nice, fresh copy of Ubuntu 9.04 from scratch.  If this is a computer you acquired, then why not make it your own!  Download the official release from here:  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))  Simply backup the contents of your /home/username (where username is YOUR username) to a USB key first.  Be sure to grab important hidden files like .mozilla, .evolution, .purple, etc.  Good luck!

---

### Post by michy99 on 2009-06-25
It is very possible that the delay on your grub menu is set to 0, which means you won't see it. Since you can get into your system, what is the output of this command in terminal?```
cat /boot/grub/menu.lst
```

---

### Post by Xeginy on 2009-06-25
Michy99 - I'm not sure I understand your question.  Like I said before, I'm a new Linux/Ubuntu user.  Am I supposed to type that code somewhere?

---

### Post by Xeginy on 2009-06-25
Michy 99 - Nevermind, I found it.  I typed in the code, and it told me "No such file or directory"  Does that mean I don't have grub?

---

### Post by michy99 on 2009-06-25
Open a terminal. Applications->Accessories->Terminal. Type in the command in th post above. Copy the response and paste it in a reply here.

Also, is your computer by any chance a Dell Mini 9?

---

### Post by michy99 on 2009-06-25
> **Xeginy said:**
> Michy 99 - Nevermind, I found it.  I typed in the code, and it told me "No such file or directory"  Does that mean I don't have grub?

make sure that it is lst as in list not 1st as in first.

---

### Post by Tyke91 on 2009-06-25
are you copy/pasting it?

Ubuntu comes with grub pre-installed... there's a chance that somebody installed lilo instead for some strange reason. but to be sure, copy/paste the command above. if that doesn't work, then try this one.

```
cat /etc/lilo.conf
```

---

### Post by Xeginy on 2009-06-25
My computer is an Asus Eee PC 901.

The entire line of code (I'm using a separate computer, my laptop is sitting to the side of me) is:

cat: /boot/grub/menu.1st: No such file or directory

---

### Post by Tyke91 on 2009-06-25
> **Xeginy said:**
> My computer is an Asus Eee PC 901.

The entire line of code (I'm using a separate computer, my laptop is sitting to the side of me) is:

cat: /boot/grub/menu.1st: No such file or directory

it's lst as in LST :)

PS: when someone gives you code, you should copy/paste it :)  this avoids confusion between 1/l/I and  ` and '  and tons of other things :P 
PSS: DOH! just read your post more :( yeah. if you're on a separate computer, you're gunna have to be careful with that

---

### Post by Xeginy on 2009-06-25
Okay!  I typed in the code right, and here is what came up...

tamarack@tamarack-laptop:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory
tamarack@tamarack-laptop:~$ cat /boot/grub/menu.lst
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
timeout        0

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
# kopt=root=UUID=151084dd-4cdc-4067-9181-73e05ff7d1fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=151084dd-4cdc-4067-9181-73e05ff7d1fe

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

title        Easy Peasy 1.0, kernel 2.6.27-8-eeepc
uuid        151084dd-4cdc-4067-9181-73e05ff7d1fe
kernel        /boot/vmlinuz-2.6.27-8-eeepc root=UUID=151084dd-4cdc-4067-9181-73e05ff7d1fe ro quiet splash 
initrd        /boot/initrd.img-2.6.27-8-eeepc
quiet

title        Easy Peasy 1.0, kernel 2.6.27-8-eeepc (recovery mode)
uuid        151084dd-4cdc-4067-9181-73e05ff7d1fe
kernel        /boot/vmlinuz-2.6.27-8-eeepc root=UUID=151084dd-4cdc-4067-9181-73e05ff7d1fe ro  single
initrd        /boot/initrd.img-2.6.27-8-eeepc

title        Easy Peasy 1.0, memtest86+
uuid        151084dd-4cdc-4067-9181-73e05ff7d1fe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


That's long, and I have no idea what it means...

---

### Post by Tyke91 on 2009-06-25
see the line that says timeout?

change that number to something like 10

doh again... just realized you don't have root access...

Try holding down escape or tapping it frequently while you are booting up. if that doesn't work, you will need to download another linux CD (ubuntu will be just fine), mount your hard drive, go to /boot/grub/menu.lst and edit the line yourself.

---

### Post by 3Miro on 2009-06-25
Applications -> Accessories -> Terminal (it looks like DOS if you have ever seen this, but it is way more than DOS).

Google Linux Terminal and see some of the basics. Many people give advice to use it since it is easier than "click here, click there, select xyz".

---

### Post by michy99 on 2009-06-25
Just as I suspected, the timeout is set to 0, which is why you don't see the menu when you boot. Do you have a cd drive and an Ubuntu Live CD? I think you will need it to fix this.

---

### Post by Xeginy on 2009-06-25
I don't have a CD drive OR a Ubuntu Live CD.  Dammit, are you sure there is no other way around this?

---

### Post by Tyke91 on 2009-06-25
> **michy99 said:**
> Just as I suspected, the timeout is set to 0, which is why you don't see the menu when you boot. Do you have a cd drive and an Ubuntu Live CD? I think you will need it to fix this.
heh... not only is his timeout 0, but the menu is hidden (he would have to press escape as well)

whoever set up the machine knew what he wanted :P

you will need some sort of live environment if you don't know the password.


ALTERNATELY, you could look up the hash for his user's password in /etc/shadow and then try to crack it with a rainbow table or something... but it would be ALOT easier just to install a new OS.

---

### Post by Xeginy on 2009-06-25
A live environment?  Like, I need to install a completely new operating system?  If I downloaded Ubuntu 9.6 (or whatever it is) would that suffice?  Because I downloaded it, it's just telling me I need to burn it onto a CD before I can officially install it, and this little laptop doesn't have a CD drive.  Besides, what if I need administrator access to install it?

---

### Post by michy99 on 2009-06-25
Can it boot from a usb drive?

---

### Post by Xeginy on 2009-06-25
...I have a USB drive.  And a USB with plenty of space on it.  I have no idea whether or not Ubuntu will boot from a USB drive; I was just going off the directions on the website.

---

### Post by nightmare0 on 2009-06-25
press escape in the grub bootloader and select the recovery kernel.. then drop to root.. does it let you drop to root?

---

### Post by Xeginy on 2009-06-25
Nightmare0 - I tried that already.  My timeout for grub is set to 0, so...yeah, I can't really do it that way.

---

### Post by michy99 on 2009-06-25
> **nightmare0 said:**
> press escape in the grub bootloader and select the recovery kernel.. then drop to root.. does it let you drop to root?

He can't get to the grub menu because the timeout is set to 0.


The only question is whether the computer can boot from usb. Check the bios set-up.

---

### Post by nightmare0 on 2009-06-25
> **Xeginy said:**
> Nightmare0 - I tried that already.  My timeout for grub is set to 0, so...yeah, I can't really do it that way.

sorry forgot about that.. yeah.. i guess you'd need a usb or live cd..

---

### Post by Xeginy on 2009-06-25
So how do I check if the computer can boot from a USB?  Should I just try it and see?

---

### Post by nightmare0 on 2009-06-25
> **Xeginy said:**
> So how do I check if the computer can boot from a USB?  Should I just try it and see?

Plug a USB in.. boot the computer and then check the boot order settings in your BIOS.

---

### Post by michy99 on 2009-06-25
> **Xeginy said:**
> So how do I check if the computer can boot from a USB?  Should I just try it and see?

That would work if you have a bootable usb drive handy. The easiest way is to start the computer and go into the bios set-up. When you start the computer, hold down the F1 key and see if that does it. If not, try Esc or Delete. Once you get to the bios menu, look for boot sequence or something like that and see if usb is listed. If it is, make sure it is first in the sequence.

---

### Post by michy99 on 2009-06-25
I've got to go take care of some business, but I will check back later to see how it is going. Meanwhile, check out these pages:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

---

### Post by bodhi.zazen on 2009-06-25
If your grub time out is set to 0 you need to rapidly mash on the esc key as you boot.

---

