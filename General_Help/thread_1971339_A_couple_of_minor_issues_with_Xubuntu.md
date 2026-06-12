---
title: "A couple of minor issues with Xubuntu"
date: 2012-05-02
forum: General Help
---

### Post by xeddog on 2012-05-02
I just went through the process of upgrading my Ubuntu 10.10 system to 11.04 to 11.10 to 12.04 and so far everything has gone well.  After upgrading I tried to like Unity but I just couldn't do it so I installed the xubuntu-desktop padkages and I am using that now.  MUUUCH better.

But there are just a couple of minor things that I have not been able to resolve yet.  

1.  Whenever I boot the system now, Nautilus will open two windows to my home directory.  How do I stop that?

2.  This "problem" has been around for a long time and was even present in 10.10.  I would like to make the window borders a pixel or two wider so it would be easier to manipulate the window size.  Right now it seems like the borders are only one or two pixels wide which makes it a pain to resize windows sometimes.

Thanks,

Wayne

---

### Post by Bucky Ball on 2012-05-02
1. Do you mean when you get to the desktop there are two /home folders opened by Nautilus? If so, close them, go to restart and on the restart window tick 'Save setup for future boots' or whatever it is (you'll see it). 

2. Can't help you.

You might want to try Xubuntu's default file manager Thunar, or for something probably lighter, lxde's pcmanfm. One of them might be more configurable re. your border issues.

---

### Post by Toz on 2012-05-02
> **xeddog said:**
> 
2.  This "problem" has been around for a long time and was even present in 10.10.  I would like to make the window borders a pixel or two wider so it would be easier to manipulate the window size.  Right now it seems like the borders are only one or two pixels wide which makes it a pain to resize windows sometimes.

You have 2 Options:
1. Use a window manager theme that comes with wider borders.

2. Look at the files in /usr/share/<THEME>/xfwm4 (where <THEME> is the name of the window manager theme you are using) and edit with a graphic editor (e.g. gimp) the files that are used to create the border.

I am unaware of a configuration setting that can accomplish this.

---

### Post by xeddog on 2012-05-02
Regarding the two home directory listings that open when I boot, I seem to have made a mountain out of a mole hill.  When I wrote this I would get one IM window (Gyachi) which I want, and Nautilus would open two windows with the directory listing of my home directory which I didn't want. 

After restarting using the save sessions dialog thing, I did get my one IM window and one Nautilus window.  But DesktopNova quit and all I got for a wallpaper was a black screen.  When I moved the Gyachi window, it kept getting redrawn  but the old copy never did get deleted so I would have images of billions of gyachi windows when I moved the original window.

 After booting into Unity 2D and then back to Xubuntu, the redraw problem went away and Desktopnova started working again, but I now get TWO copies of Gyachi opening and one Nautilus.  And of course the second Gyachi fails because of socket errors or somesuch.  I tried restarting using the save session option again and now nothing changes.

Rats!

Wayne

---

### Post by xeddog on 2012-05-03
A new day and things have settled down somewhat.  I am back to where I started minus one Nautilus window which means that when I boot now, I get my IM window and only one Nautilus window.  I think I am going to let well enough alone now.  At least for now.


Wayne

---

