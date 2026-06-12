---
title: "Ubuntu not loading (wubi)"
date: 2011-08-31
forum: General Help
---

### Post by Ichinenjuu on 2011-08-31
I'm pretty new to Ubuntu and I wanted to install it using wubi on my Sony VAIO CA. I installed everything, rebooted the computer, selected "Ubuntu" under the boot menu, then under the GNU Grub, selected the first Linux option (not the recovery mode option) and it takes me to a black screen with various lines of white text and it will go no further and will not load Ubuntu.

The last time of text is:

[ 13.548610] type=1400 audit(1314752145.392:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=780 cinn="apparmor_parser"

So...what does this mean? I know I can install it using a CD, I just don't have any blank CDs right now and wanted to try this method. How come it isn't working?

---

### Post by jfed on 2011-08-31
No clue

BUT

You don't need a CD, you can install it off of a LiveUSB!

```
sudo apt-get install unetbootin
```

Just download the .iso, launch unetbootin, select iso (not the pre-set distro thing) and browse to the iso.

The file browser is a little unconventional, but its not that hard to understand, it starts you off in root or something, just go to your hard drive, then home, simple.

oh well and of course you need to have the usb drive in the port, but its quite simple, as long as you don't have any other mass storage devices plugged in it should auto-recognize your usb drive

---

### Post by Ichinenjuu on 2011-08-31
Well, I just tried that, but no luck.

It started to install then it came up with this:

(initramfs) Unable to find a medium containing a live file system

Any thoughts on this? Or is my computer just trying to tell me that installing Ubuntu is just not going to happen?

In a couple days when I get access to some blank CDs, I'll try again. I have installed Ubuntu before on other computers, but each time I used a blank CD. I've never tried another method; I just wanted to see if something else would work.

---

### Post by jfed on 2011-08-31
Perhaps you either,
A didn't have adequate space on the drive
B wasn't the right filesystem

You can try using Gparted to format it to Fat32, then re-installing, or you could just wait of course haha. Thats what I would do as I have a deep hatred for Wubi :lolflag:

---

### Post by Ichinenjuu on 2011-08-31
There was definitely enough space, it's a blank 32 GB USB drive. I formatted it and tried reinstalling it using unetbootin, but this time it encountered an error saying something about the "wrong volume" and giving an option to cancel, try again, or cotinue, so I clicked continue and it finished installing and asked if I wanted to reboot. I rebooted and tried to load from the USB drive but nothing happened. Just a blinking white bar.

I think I'm gonna cry :(

Oh well, I tried everything I could with what I have now and nothing worked. Thanks for your help, though :)

---

### Post by Ichinenjuu on 2011-08-31
Just for reference, this is what appears when I try to install Ubuntu:

[IMG]http://i242.photobucket.com/albums/ff293/Onnajanai/IMAG0085-1.png[/IMG]

Makes me wonder if the word "radeon" appearing so much means that my shitty graphics card is preventing me from installing Ubuntu...God I hope not...

---

### Post by bcbc on 2011-08-31
Try adding the 'nomodeset' kernel boot option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Then if it works see if you require a custom driver for your graphics card.

If that doesn't work post full specs including graphics card - and also the release you are installing.

Also you can review this - maybe it will help: [http://ubuntuforums.org/showthread.php?t=1752202](http://ubuntuforums.org/showthread.php?t=1752202)

(The particular problem you are having will be the same on a direct install, since Wubi is different only in the virtual disk and the 'jump start' using windows/grub4dos. In other words, reinstalling won't magically resolve the problem, however once you figure out what the workaround is you can apply the same to a direct install).

---

### Post by Ichinenjuu on 2011-08-31
So...I did what you said, then I got this message:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment. "

It then loaded Ubuntu and got to the desktop and seems to be working. Then a "Additional Drivers" notification popped up and it's asking me if I want to activate the ATI/AMD proprietary FGLRX graphics driver. Is that what was causing the problem? Should I not activate it?

---

### Post by bcbc on 2011-08-31
It's probably dropping to the Classic because of the nomodeset. 

Normally - with a dedicated graphics card you would enable the graphics driver, but if you have a dual graphics card (onboard intel and ondemand gpu) then this will not work. With Ubuntu you have to use the intel - as far as I know ondemand gpu's aren't supported yet). So that other thread that talked about blacklisting the radeon may be what you need to do. After that you shouldn't need the nomodeset option to boot and probably the Unity desktop will work.

But I'm not sure what your setup is, so the above is just a guess.

---

