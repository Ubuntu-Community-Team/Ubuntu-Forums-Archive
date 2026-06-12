---
title: "I finally got Ubuntu installed and now I need help setting up my video drivers"
date: 2006-06-22
forum: General Help
---

### Post by Aardfox on 2006-06-22
Thank you so much for all your help with my getting past the black screen issue.

I finally got Ubuntu installed but now I'm seeing more driver issues.
I have a few questions:
1) Are there any ATI radeon drivers that have been ported to linux?
2) Once I burn these drivers onto a CD (assuming they exist) how do i access the CD and install the drivers without booting the GUI? 

Thanks

---

### Post by gerbman on 2006-06-22
This should help, depending on your card:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Aardfox on 2006-06-22
So I download the fglrx driver, burn it to a cd, put the cd in, and type in those exact commands and it will find it on the cd and work?

And how do i boot in console so I can circumvent the GUI, where it crashes?

Thanks

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]So I download the fglrx driver, burn it to a cd, put the cd in, and type in those exact commands and it will find it on the cd and work?

And how do i boot in console so I can circumvent the GUI, where it crashes?

Thanks[/QUOTE]Not quite. Just follow the directions under "Install instructions for Ubuntu 6.06". All of those commands go into the terminal window (Applications->Accessories->Terminal).

---

### Post by Aardfox on 2006-06-22
I can't get to the terminal, that's part of the problem. I have to do this in a way that A. doesn't require me to be connected to the internet to get the drivers (which is why I think I need to burn the drivers to a CD) and B. lets me install them without getting to the GUI part of ubuntu.

I'm using Windows right now, and Ubuntu on my other hard drive.

Thanks

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]I can't get to the terminal, that's part of the problem. I have to do this in a way that A. doesn't require me to be connected to the internet to get the drivers (which is why I think I need to burn the drivers to a CD) and B. lets me install them without getting to the GUI part of ubuntu.

I'm using Windows right now, and Ubuntu on my other hard drive.

Thanks[/QUOTE]Sorry, didn't catch that. That might be a problem because there are a number of other packages that need to be installed...not just linux-restricted-modules and xorg-driver-fglrx. Normally, the package manager identifies any dependencies and downloads/installs them automatically. I'm at a loss for an easy solution. You could download all of the packages manually, burn them to CD, and do it that way. Here is the list for linux-restricted-modules:

[http://packages.ubuntu.com/dapper/misc/linux-restricted-modules-2.6.15-25-386](http://packages.ubuntu.com/dapper/misc/linux-restricted-modules-2.6.15-25-386)

and here is the list for xorg-driver-fglrx:

[http://packages.ubuntu.com/dapper/misc/xorg-driver-fglrx](http://packages.ubuntu.com/dapper/misc/xorg-driver-fglrx)

If you're serious about doing it this way I can give you more pointers. Do you get any error messages when Ubuntu crashes while booting?

---

### Post by Aardfox on 2006-06-22
No errors. I'll explain exactly what happens every time: I get to the GUI login screen and as I'm typing aardfox into the login box the colors for the lettering are a bit off. There's a blue "a" to the right of the text black "a" and a red "a" to the left, so it's like I'm seeing triples. After typing a few letters the whole screen just freezes. Game over :)
I'm assuming this is a graphics problem... 

How do I boot Ubuntu in a console and what's the command for accessing a CD?

Unfortunately I won't be able to attempt this until tommorow as I am no longer near my linux computer, but thanks again.

---

### Post by gerbman on 2006-06-22
> How do I boot Ubuntu in a console and what's the command for accessing a CD?When you get to the login screen, hit CTRL+ALT+F1. That should get you to a terminal login.

---

### Post by Aardfox on 2006-06-22
How do I access the CD with the copied drivers?

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]How do I access the CD with the copied drivers?[/QUOTE]First check /etc/mtab to make sure the CD isn't already mounted. If there isn't a line containing "cdrom" then you need to mount the CD manually. You should be able to do this with the following:```
sudo mount /media/cdrom
```where /media/cdrom is the directory where you want to mount the CD at. If this works, then you should be able to read the CD by looking through the /media/cdrom folder.

---

### Post by grendelkhan on 2006-06-22
The new installer has me all discombobulated.  When the pool directory used to just contain all the packages, fglrx and linux-restricted-modules were there.  I can't read the installer's squashfs to see what all gets installed now.

Why can't you connect to the net?

---

### Post by Aardfox on 2006-06-22
Thanks a gajillion man! Do you ever sleep?
I'm using a wireless Netgear card and it isn't being detected.
I'll figure that out once the OS is working though, no prob.

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]Thanks a gajillion man! Do you ever sleep?
I'm using a wireless Netgear card and it isn't being detected.[/QUOTE]Haha, sometimes. Post back with your results - I'm curious to hear if that actually works (though I'm not sure what was causing the video problems to begin with).

---

### Post by Aardfox on 2006-06-22
I am now posting, using firefox, in Ubuntu. Victory is ours!

Apparently my internet DOES work. While I was going through the Install instructions for Ubuntu that you posted in the first link, it started downloading the apt-get stuff from the net. I guess I lucked out there :)

However, once I got to the part where I had to sudo gedit /etc/X11/xorg.conf I got an error that was something like: Could not open xorg.conf (null). 

I wonder why it works even when I stepped the last half of the instructions because of this...I guess downloading the update was enough.

Any idea what's wrong with sudo gedit /edit/X11/xorg.conf ?

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]Any idea what's wrong with sudo gedit /edit/X11/xorg.conf ?[/QUOTE]It should be /etc not /edit, but I'm assuming that was a typo in your post. What is the output of```
ls /etc/X11 | grep xorg
```

---

### Post by Aardfox on 2006-06-22
Now that I finally got into the GUI, I tried doing this in the terminal and gedit /etc/X11/xorg.conf worked. So I scrolled down to the "screen" section but it was already edited in the way that the website wanted me to edit it.
I guess the update I downloaded had it configured correctly.
I am sooooo happy you helped me with this.

---

### Post by gerbman on 2006-06-22
[QUOTE=Aardfox]Now that I finally got into the GUI, I tried doing this in the terminal and gedit /etc/X11/xorg.conf worked. So I scrolled down to the "screen" section but it was already edited in the way that the website wanted me to edit it.
I guess the update I downloaded had it configured correctly.
I am sooooo happy you helped me with this.[/QUOTE]That's what this forum is here for :) Pass it on!

---

