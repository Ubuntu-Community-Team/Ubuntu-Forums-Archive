---
title: "Switch to VirtualBox"
date: 2010-09-20
forum: General Help
---

### Post by grnorris on 2010-09-20
I currently have both Windows 7 (32 bit, thinking of going 64) and Ubuntu 10.04 (64 bit) dual booted on my machine.  I was thinking (for hardware and some software compatibility reasons) of switching to using Ubuntu in a virtual Only environment.  If I do then my Emulator of Choice is Virtual Box as I figure I can eventually set up seamless mode.  What I need to know is if there's a easy way to get my settings and programs into a virtual environment.  Obviously I wouldn't need all of my programs since some of them are specific to my real hard ware and some of them are probably junk from programs I tried and didn't like but, I do need to keep all the save files for games and such.

The main things I use Ubuntu for are games (Just love Linux games), some programming, and possibly a little hacking (Legal of course).

If I'm going to switch to this Virtualized setup I'll need to do so before I can switch my Windows to 64-bit.  This way I can more easily repartition/format my hard drive (I'll also need to do a long format to check for errors I think chkdsk and similar are missing).

---

### Post by grnorris on 2010-09-21
I hate to do this but, BUMP.  I could really use advice here.

---

### Post by maestrobwh1 on 2010-09-21
I am not sure if this will work, but I will toss out the ideas.  

Could you clone your disk to an image on a usb device, using clonezilla-live, then run the the clonezilla iso in virtualbox with the usb device enabled, and dump the contents onto a virtual disk of greater size than the original ubuntu partition?


It would be very slow.  You could also perhaps use tar and tar up your current partition (to a usb device again), then do something similar by launching a live cd in virtualbox and untarring the potentially very large tarball to a formatted ext3 or ext4 virtual partition... then install grub2.

Just some ideas.

---

### Post by clhsharky on 2010-09-21
grnorris

3D in Virtual Box or any virtual machine is very poor.
Many if not most 3D games are unplayable on virtual hardware be it windows or Linux.

Sharky

---

### Post by grnorris on 2010-09-22
I know 3D can sometimes be slow but, I'm hoping my 3D acceleration hardware takes care of that.  As for methods of installing I was thinking maybe some way to create a custom repository to 'download' from (Like APTON CD) then maybe copy my home directory.  I'm fairly sure this would work but, I was hoping for an easier and more guaranteed way (not all apps store data in the home directory + I'm not sure if my file encryption will interfere(It's the normal Ubuntu encryption that it prompts you about when you install Ubuntu)).

I know a friend of mine runs Ubuntu in a virtual environment and he hasn't reported any real problems though he does have an entirely different set of hardware.  He also started in a virtual machine because his machine can't use Ubuntu at all with it's normal hardware.

---

### Post by bodhi.zazen on 2010-09-22
> **grnorris said:**
> I know 3D can sometimes be slow but, I'm hoping my 3D acceleration hardware takes care of that.

It will not as virtual machines do not directly use your hardware.

---

### Post by BobVila on 2010-09-22
> **grnorris said:**
> I know 3D can sometimes be slow but, I'm hoping my 3D acceleration hardware takes care of that.  As for methods of installing I was thinking maybe some way to create a custom repository to 'download' from (Like APTON CD) then maybe copy my home directory.  I'm fairly sure this would work but, I was hoping for an easier and more guaranteed way (not all apps store data in the home directory + I'm not sure if my file encryption will interfere(It's the normal Ubuntu encryption that it prompts you about when you install Ubuntu)).

I know a friend of mine runs Ubuntu in a virtual environment and he hasn't reported any real problems though he does have an entirely different set of hardware.  He also started in a virtual machine because his machine can't use Ubuntu at all with it's normal hardware.

VBox's already iffy 3d support only works with Windows guests, so game performance will be pretty crappy.

---

### Post by grnorris on 2010-09-22
> **BobVila said:**
> VBox's already iffy 3d support only works with Windows guests, so game performance will be pretty crappy.

Even if the software support doesn't work for Ubuntu my machine may still be powerful enough to make most of the games work.  The only real 3D game I've tried is a Tron game (TronGL I think).  Otherwise it's just games like Super Maryo Chronicles.  In any case I'd like to try it before I just say it won't work.  If I can get Ubuntu working in this configuration then I couldn't avoid issues with my wireless and graphics card (issues that Windows doesn't have).

In any case any easy ways to getting my data to a new machine.  Probably the same methods used to transfer to new computer.

---

### Post by wilee-nilee on 2010-09-22
I would just go ahead and install a Ubuntu to the Vbox and try it first. At this point it is all speculation, check it out and then proceed from there. 

You can save a script of all the installs in your dual booted Linux if it needs to be the setup in the virtual, and if you can't transfer the OS itself.

---

