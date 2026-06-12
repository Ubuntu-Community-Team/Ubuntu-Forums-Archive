---
title: "Grub with Debian universal operating system background"
date: 2012-01-14
forum: General Help
---

### Post by Canaryguy on 2012-01-14
Hello,

When I turned on the computer today I saw that Grub 1.99 has a new background with a world, stars and the Debian logo in the upper right corner and saying "Debian the universal operating system" in the lower right corner. But I haven't installed Debian. Is this normal?

---

### Post by drs305 on 2012-01-14
I've come across this background from time to time, although I don't use Lubuntu. The image file may be called *moreblue-orbit-grub.png*

Since I assume you didn't add it yourself, you can inspect the /boot/grub/grub.cfg or /etc/grub.d/05_debian_theme to see where this file is being imported from. 

Normal sources might include simply having the image file in /boot/grub, where the latest Grub 2 versions will automatically place the image in the background, or in /usr/share/images/grub. 

It's also possible it was installed if you added the 'desktop-base' package. I don't have it installed, but I think it's located in /usr/share/images/desktop-base once it is.

---

### Post by Canaryguy on 2012-01-14
Maybe the background changed after I installed Gnome 3 yesterday. That was the only thing I installed.

---

### Post by hhh on 2012-01-14
> **Canaryguy said:**
> Maybe the background changed after I installed Gnome 3 yesterday. That was the only thing I installed.
"The only thing" includes something like a hundred dependencies?

The Grub theme and wallpaper are named "spacefun" (Debian Spacefun is the theme name) and on my Debian system the wallpapers are located in /usr/share/images/desktop-base, /usr/share/plymouth/themes and /usr/share/splashy/themes and probably were pulled in by a plymouth upgrade.

---

### Post by bogan on 2012-01-14
Hi!, **canaryguy**, and** drs305**

You Posted :> When I turned on the computer today I saw that Grub 1.99 has a new  background with a world, stars and the Debian logo in the upper right  corner and saying "Debian the universal operating system" in the lower  right corner. But I haven't installed Debian. Is this normal? and :>  Maybe the background changed after I installed Gnome 3 yesterday. That was the only thing I installed.     I too found I had the Debian background after installing Gmome3, but not as a background to the Grub Menu, nor to the Desktop.
I t appeared as soon as the Grub screen closed and stayed until the Login screen opened.

I wish it had stayed that way, rather than 25 seconds of Blank Black screen. But when Update Manager upped from 11.10 -12 to -14 it disappeared.

Is there anyway to get it back ? 
or to put some other background to show during the boot sequence  following the Grub boot screen?

Chao!, **bogan.**

---

### Post by Canaryguy on 2012-01-14
> **bogan said:**
> Hi!, **canaryguy**, and** drs305**

You Posted : and :I too found I had the Debian background after installing Gmome3, but not as a background to the Grub Menu, nor to the Desktop.
I t appeared as soon as the Grub screen closed and stayed until the Login screen opened.

I wish it had stayed that way, rather than 25 seconds of Blank Black screen. But when Update Manager upped from 11.10 -12 to -14 it disappeared.

Is there anyway to get it back ? 
or to put some other background to show during the boot sequence  following the Grub boot screen?

Chao!, **bogan.**

When I turned on the computer for the first time today I think I saw this background even before the grub menu ...or not, I didn't pay much attention since I didn't expect it. I have installed Gnome 3 on previous occasions and the Grub appearance has never changed till now.

---

### Post by praveen2311 on 2012-05-16
can we change that image ? . If so, how to do it? please help!! 

Thanks in advance

---

### Post by Ubun2to on 2012-05-16
> **Canaryguy said:**
> Maybe the background changed after I installed Gnome 3 yesterday. That was the only thing I installed.

When I had 11.10, I installed Gnome 3, and it changed the boot screen to that same background. When I upgraded to 12.04, it went away, and Gnome 3 hasn't done that to me.

---

