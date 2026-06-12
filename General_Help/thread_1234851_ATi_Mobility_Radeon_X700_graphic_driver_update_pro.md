---
title: "ATi Mobility Radeon X700 graphic driver update problem on Ubuntu 9"
date: 2009-08-08
forum: General Help
---

### Post by ash4ever on 2009-08-08
Hi guys,

I hope that someone can help me on the forum. I've just bought Prey and installed it on my Acer laptop which installed great and started great. But once you try playing the game, the graphics goes grey and you can't see anyting but can hear that the game is on. 

Can someone, please tell me how i can upgrade my ATi Mobility Radeon x700 graphics card driver for my laptop?

For those wondering on how i'm playing the game, i'm using wine :)

AN

---

### Post by spoons on 2009-08-08
You'll need to install Fglrx if you're using the OSS driver.

---

### Post by handy on 2009-08-08
This thread may help:

[http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+closed+drivers](http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+closed+drivers)

tseliot is the man for graphic drivers & Ubuntu.

---

### Post by del_diablo on 2009-08-08
Why does nobody EVER read the news?
If your running Ubuntu 9.04, then you can only use the open drivers.
With 8.10 or earlier you can use driver version up to 9.3

Edit: with the AMD(read: propitary) driver installed, run "sudo aticonfig -initial"  to make sure that you get a proper xorg config.

---

### Post by ash4ever on 2009-08-08
Hi guys,

Thanks for helping me out. I tried following the steps for **Instructions for Ubuntu 9.04 (Jaunty)** which say:

Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then do:  - **This part there is nothing displayed there.**

Then did the next step: sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
[B]This gave me the following out of the terminal - update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
[/B]

Then the last step, sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
Which gave me the following **insmod: can't read '/lib/modules/2.6.28-11-generic/volatile/fglrx.ko': No such file or directory**

Maybe, i'm just stupid, but i can't seem to get this to work. If you can help thanks but if you can't, thanks for trying.

AN

---

### Post by oldrocker99 on 2009-08-08
This is why I'm still running the 9.03 drivers on Intrepid (8.10).

9.04's open source drivers were just too slow compared to ATI's. I hope you get your problem straightened out. I'd love to use 9.04 myself.

:guitar:

---

### Post by handy on 2009-08-08
I use Arch, & recently the 2D of the Open drivers has become the best there is, for most ATi GPU's.

The 3D is starting to happen with the ATi Open drivers also.

It won't be too long & AMD/ATi's GPU's will have the best support in the game.  But they aren't there yet.

Sorry I can't help the OP anymore, I'm not using any Ubuntu's at the mo' apart from a Mint-6-Xfce (very rarely) which actually set up my nVidia machine (with the nVidia card from hell in it) correctly & automatically using the proprietary drivers on installation.

Mint really is impressive as far as polishing up Ubuntu is concerned, imho. :)

---

### Post by deadmnky on 2009-08-09
not too positive on ati graphics but have you tried to install prey with the installer designed for linux
try this link see if it helps any

[http://icculus.org/prey/downloads/prey-installer-02192009.bin](http://icculus.org/prey/downloads/prey-installer-02192009.bin)

---

### Post by ssri on 2009-08-09
> **del_diablo said:**
> Why does nobody EVER read the news?
If your running Ubuntu 9.04, then you can only use the open drivers.
With 8.10 or earlier you can use driver version up to 9.3

Edit: with the AMD(read: propitary) driver installed, run "sudo aticonfig -initial"  to make sure that you get a proper xorg config.

That is untrue, one could install Catalyst 9.3 on Jaunty, as I did.  However, it involves downgrading xorg-xserver (easy) and a whole lot of CLI and xorg.conf kung-fu to get my ATI card working.  I was initially unhappy with Jaunty's radeon and radeonhd offerings.  Also, the latest git checkout did not result in the performance I hoped it would.

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by ash4ever on 2009-08-10
Hi guys,

Thanks for all the help. Going to download 8.04 and see what happens. 

Will keep you guys updated. I think that the new version is pretty stupid if I can say that, if it can't cater for ATI graphics cards and have an option to update the software. But I still love Ubuntu.

AN

---

### Post by handy on 2009-08-10
ATi's Catalyst driver package has been wobbly; sometimes the new versions are much worse than the ones they replace. The Catalyst drivers have been very unreliable this year, especially lately.

Anyway, we won't have to wait too much longer for the Open drivers to do great 3D, when that happens it will be a new day. :KS

---

### Post by ash4ever on 2009-08-10
Have to agree with you handy. 

This is not the ideal fix, but the problem has been resolved. I had to install Ubuntu 8.04 and use the ATi driver update and now the graphics for the game works fine and without any problems. 

This is a step back from a technology point of view and hope that the Ubuntu team can fix this before the next installment of Ubuntu.

AN

---

### Post by martinbaselier on 2009-08-10
The ubuntu team can't fix this, since it's ATI's decision not to support the card anymore. It's possible to downgrade your xorg. I happen to have an x700 too, and my experience is that it works better with the opensource drivers. 

Here's how to downgrade it:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

I would advise to stick to the ati driver in the 8.04 version though, since it has a problem on the x700 in intrepid, at least with xfce. My icons keep disappering when I use the ATI driver. Plus my whole system feels less responsive.

---

### Post by ash4ever on 2009-08-10
Thanks. Yeah i used the default Ubuntu update and that worked fine for me.

---

### Post by DeLiK on 2009-10-26
I Have the same exact problem
This ATI Xorg2 conflict drives me mad...

---

