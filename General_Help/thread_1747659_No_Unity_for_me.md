---
title: "No Unity for me?"
date: 2011-05-02
forum: General Help
---

### Post by M1ke on 2011-05-02
I'll admit I've not been that keen on the look of Unity from the outset, but I want to give it a fair shout before deciding whether it's my thing. Unfortunately the current version of virtualbox doesn't appear to play nicely with gnome 3 and on creating an 11.04 live usb I've still not been able to try it out.

On booting the live usb on this machine I'm given the "classic" desktop, presumably because I'm somehow not meeting the requirements for Unity. I get no error messages or clues as to why though.

My graphics card is an nVidia GeForce G210M (512MB) and has no trouble with all the pretty compiz effects under Ubuntu 10.04 and 10.10, so is the problem something else or are the requirements for Unity really that high?

---

### Post by hansdown on 2011-05-02
Hi M1ke.

The nVidia cards are causing some problems.

Are you able to install the drivers?

---

### Post by M1ke on 2011-05-02
I did wonder if drivers were the problem; on checking the system admin menu it didn't offer any. Why might that be?

---

### Post by hansdown on 2011-05-03
Possibly, there are none at this time.

Softpedia has some, but be careful to match the right one.

[http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml](http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml)

This link is for** Nvidia 270.41.06 **

---

### Post by plucky on 2011-05-03
> **M1ke said:**
> I did wonder if drivers were the problem; on checking the system admin menu it didn't offer any. Why might that be?

Do you have a network connection?

Are all the repositories enabled for the Live USB?

---

### Post by M1ke on 2011-05-03
Yeah, I have a connection and I've enabled the necessay repos. Will take a look at the link when I can and let you know, cheers!

---

### Post by coppertrail on 2011-05-03
Did you enable 3D video support in your VirtualBox guest? Go into the guest settings, click on display and make sure that "Enable 3D acceleration" is checked. Power the guest back on and Unity should appear (as long as you have the VirtualBox Guest Additions installed)

---

### Post by M1ke on 2011-05-06
> **coppertrail said:**
> Did you enable 3D video support in your VirtualBox guest? Go into the guest settings, click on display and make sure that "Enable 3D acceleration" is checked. Power the guest back on and Unity should appear (as long as you have the VirtualBox Guest Additions installed)

I thought I'd tried that but can't be sure so I'm reinstalling on the guest now (yeah, I wiped it when it all looked like it wasn't going to play nice). I've made sure to check that box and assign as much video memory as possible.

I've installed guest additions in Windows machines before, is it done the same way for linux machines? Machine menu > Install guest additions?

---

### Post by YesWeCan on 2011-05-06
I have tried what you are trying.

I burned the 11.04 32 bit live ISO to a USB stick with 500MB persistent memory. It didn't like my video card either and booted into Gnome 2. I had to go to the Ubuntu software centre and search for nvdia drivers and then I chose the one that looked a likely candidate for my 6600GT - it was the 173 (I think). Still running off the live USB I installed it. When I rebooted back to the USB it then came up in Unity. It now appears to work as it is supposed to.

I tried to use 11.04 as a guest OS in VirtualBox. Immediately after creating the VM I changed the Display settings to enable 3D acceleration and I set the video memory to a max of 128MB. Then I ran the VM and chose the iso file to boot and it booted up. I cannot wuite recall whether it booted fine at this point or whether I had to install 4.06 Guest Additions and then reboot. But it did work with Unity in the end...with some crashes if I tried to resize the VM window. There are general problems with Unity and Gnome Shell on VB: [http://forums.virtualbox.org/viewtopic.php?f=3&t=40893&p=185929&hilit=unity#p185929](http://forums.virtualbox.org/viewtopic.php?f=3&t=40893&p=185929&hilit=unity#p185929)

---

### Post by M1ke on 2011-05-06
> **YesWeCan said:**
> I have tried what you are trying.

I burned the 11.04 32 bit live ISO to a USB stick with 500MB persistent memory. It didn't like my video card either and booted into Gnome 2. I had to go to the Ubuntu software centre and search for nvdia drivers and then I chose the one that looked a likely candidate for my 6600GT - it was the 173 (I think). Still running off the live USB I installed it. When I rebooted back to the USB it then came up in Unity. It now appears to work as it is supposed to.

I tried to use 11.04 as a guest OS in VirtualBox. Immediately after creating the VM I changed the Display settings to enable 3D acceleration and I set the video memory to a max of 128MB. Then I ran the VM and chose the iso file to boot and it booted up. I cannot wuite recall whether it booted fine at this point or whether I had to install 4.06 Guest Additions and then reboot. But it did work with Unity in the end...with some crashes if I tried to resize the VM window. There are general problems with Unity and Gnome Shell on VB: [http://forums.virtualbox.org/viewtopic.php?f=3&t=40893&p=185929&hilit=unity#p185929](http://forums.virtualbox.org/viewtopic.php?f=3&t=40893&p=185929&hilit=unity#p185929)

This certainly sheds some light on things; I don't think I had any space reserved on the USB stick for persistent storage so even if I could find a hardware driver to download and install a reboot would have wiped it anyway.

I'm just finishing the virtual installation now and I've installed the latest guest additions, 4.06. Will see what a reboot does!

---

### Post by M1ke on 2011-05-10
Thanks for the pointers guys, but virtualbox has still given me no joy and remaking the live USB with some space for persistant storage so I could install graphics drivers didn't get me any further either (still none offered via "additional drivers" in the menus, but there are three nVidia ones in the repos). With enough time and patience I think I could probably get the unity show on the road but honestly I'm not too bothered right now, it was more out of curiosity than anything as I'll be sticking to 10.04 & 10.10 for the forseeable.

Cheers!

---

