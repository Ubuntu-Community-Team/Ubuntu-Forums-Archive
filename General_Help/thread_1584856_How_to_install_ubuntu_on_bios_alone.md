---
title: "How to install ubuntu on bios alone?"
date: 2010-09-29
forum: General Help
---

### Post by qwertyfish11 on 2010-09-29
Okay so I have a Dell XPS 600, and absolutely no working OS is installed on the machine. By that, I mean I have WinXP, but there's some error and when I run a normal boot it loads Windows Setup, but it "encounters" an error. Not that I care, I just want Ubuntu. So basically, I need to setup Ubuntu without first running an operating system. But my BIOS won't load it- I press F12 at startup and select "boot from onboard CD drive" but then it tells me that there's nothing to startup from, and I get stuck pressing F2 to retry. Btw, I used the regular 10.04 disk download, not the live CD. 
 
So, please help. Thanks  :)

---

### Post by searchfgold6789 on 2010-09-29
You have to:

[LIST]
[*]Download the image from the ubuntu website
[*]use a special program to burn the iso image to the cd
[*]boot from it
[/LIST]
You cannot simply get the iso file and burn that file directly onto the cd, you have to use an iso burning program.

---

### Post by hhh on 2010-09-29
There is no recovery drive you can boot into to reinstall XP?

If you insist on removing Windows, can you use another computer to burn the iso to a CD or DVD or to a 1G or greater USB drive (use Unetbootin for the USB)? Then just change your boot option to boot the CD (you probably won't need to change anything for that) or the USB.

---

### Post by qwertyfish11 on 2010-09-29
I do have access to another computer, so i need a specific program to burn the iso? and does it have to be the live cd, or just the plain download image?

---

### Post by Quackers on 2010-09-29
The Live cd may come in handy later (for repair purposes). If you are using a Windows machine something like ImgBurn will burn the .iso file. You need to select "burn image" or "burn iso" for it to work. And it is advisable to burn the image at a slower speed (less chance of an error burning).

---

### Post by lisati on 2010-09-29
> **Quackers said:**
> The Live cd may come in handy later (for repair purposes). If you are using a Windows machine something like ImgBurn will burn the .iso file. You need to select **"burn image"** or **"burn iso"** for it to work. And it is advisable to burn the image at a slower speed (less chance of an error burning).

I concur. If you burn it as a data disc, so that it looks like an ISO file on the disc, it won't work.
More information can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by oleink on 2010-09-29
> **lisati said:**
> I concur. If you burn it as a data disc, so that it looks like an ISO file on the disc, it won't work.
More information can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Good stuff.  Definitely used mine for repairs a few times and even helped someone get rid of a virus on a windows machine.  UBUNTU FTW.

Cheers

---

### Post by qwertyfish11 on 2010-09-30
So to recap- the problem is that i put in a plain iso file and didn't burn the iso? Thanks, seems like an easy enough fix. I'll try when I get home.

---

### Post by oleink on 2010-10-08
> **qwertyfish11 said:**
> So to recap- the problem is that i put in a plain iso file and didn't burn the iso? Thanks, seems like an easy enough fix. I'll try when I get home.

How'd it go

---

### Post by psusi on 2010-10-08
The normal desktop install cd is the livecd.  And yes, if you can see the .iso file on the cd when you try to view it, you did not burn it correctly.

---

### Post by spankler on 2010-10-08
I'm having (I think) a similar problem. I have a Dell w/ a Pentium(R) 4 2.60 GHz and ubuntu 10.04 installed, Kernel Linux 2.6.32-35-generic and GNOME 2.30.2. I want to learn linux and am *brand* new, but also need Windows for work so I am trying to set up a dual boot. I have Windows .iso disks (both XP and 7) but I can't boot from them and F1, F2...F12, esc, and del won't let me get to the BIOS screen to change the boot order. Is there just an absurdly easy way to do this that I'm just missing? BTW, both OS's wold be on the same HD. Like I said, I'm new so *any* help is *greatly* appreciated, and the more detail, the better :???:

---

