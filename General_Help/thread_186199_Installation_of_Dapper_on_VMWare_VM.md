---
title: "Installation of Dapper on VMWare VM"
date: 2006-06-01
forum: General Help
---

### Post by rcarring on 2006-06-01
This is a short list of notes:

1) I cannot believe that a single 700mb image can generate nearly 5GB of used disk space. I had a clean vm disk from a former Breezy upgraded to Dapper installation that had grown to 3GB, and thought that 3GB would be big enough for a default install from the alternate cd. I was wrong. It bloated out to nearly 4GB before VMWare reported I had run out of disk space on the host system, so I had to zap one of my XP VMs to make room.

2) Nautilus is STILL missing from the application menu. I don't see why I should have to add it manually as it is the default file manager under Gnome Ubuntu.

3) I am running with the orange and brown default theme at present, although I may change it later.

4) The install cd contained gcc compiler!!! 

5) Installing VMWare tools worked as expected, right down to compiling the modules and starting networking, except:

6) The networking start didn't start until I enabled the eth0 device and activated it.

7) The release system is a lot faster than the betas.

8) OpenOffice splash still does not have a progress bar.

Overall, I am very impressed with the quality of this release.

---

### Post by Jammy_Stuff on 2006-06-01
That's strange. Mine comes out as 2,255 MB.

---

### Post by Rackerz on 2006-06-01
Yeah mine isn't that big either, espicially not that big.

---

### Post by roger6106 on 2006-06-01
I installed mine on a 4 GB vmware image perfectly.

---

### Post by rcarring on 2006-06-01
Maybe its something to do with the image I was using.

I have found that starting from a "browser-appliance" image from the vmware site, and using that virtual hard disk, then doing a clean install led to less growth.

Having said that, it took me a while to get this VM sorted so I am not going to bother reinstalling everything to get a smaller hard disk footprint on the host, as it is inevitably going to grow anyway.

I also install a lot of stuff that others may not install such as the linux-headers and Lyx.

Thanks for the feedback.

---

### Post by TheStyle on 2006-06-04
rcarring, or anyone, could you give me the rundown on how to install vmware tools. I'm a total linux novice and last time I tried to install them on an earlier version of ubuntu I couldn't get it to work.

I'm using VMware 5.5 under XP with a fresh install of Ubuntu 6.06 as the guest.

Any help would be appreciated. Thanks.

---

### Post by TheStyle on 2006-06-05
bump

---

### Post by rcarring on 2006-06-08
You need to copy the gzipped file to your home folder and unzip it. The file may be found on the linux.iso file in VMWare Workstation.

Run the installer as sudo

Run the vmware-config

You will need gcc and make installed.

VMWare will compile modules etc and configure.

Follow the instructions on stopping and starting the network

Add vmxnet to /etc/modules

Activate and configure eth0

Reboot

Your network should now be up and running.

---

### Post by mannheim on 2006-06-08
[QUOTE=rcarring] It bloated out to nearly 4GB before VMWare reported I had run out of disk space on the host system, so I had to zap one of my XP VMs to make room.
[/QUOTE]

But 4GB is the amout of space the disk image was taking up on the host, right? As far as guest OS is concerned, you probably had less than 2.5 GB on the disk. Or did you mean that 4 GB was what the guest said was in use on the disk?

---

### Post by TheStyle on 2006-06-08
Ok I've tried to go through the instructions here: 

[edit: cut the link. I cant get it to work]

and the stuff in this thread, and absolutely nothing has gone right. There ends up being some kind of deviation almost every step of the way. I don't have time today, but maybe tomorrow I'll post what I've done step by step to see if anybody can see what the hell keeps going wrong.

This is becoming really frustrating.

---

### Post by bbruecker on 2006-06-09
Hi, I had some problems too. I miss features with Breezy Badger gives virtual guests. 
   
  First of all I like to add that it was impossible for me to install the tools within a gnome console window because a process or daemon looks some files in a init-direcetory (it seems to me – I’m very new to linux at all). I found that at other news forums: press CTRL-ALT SPACE and F2 to run the vm in console modus, and then the installation works (fine). As described above: Is it possible to install the tools within gnome-console window? Maybe this depends on the version* of vmware tools. Please post your opinion about the vms runtime modus need to install the tools. 
   
  After installation I miss many features I used to like with vmware tools at Breezy Badger vms guest: I cannot change the vms window size and I still have to put in the shortcuts to release mouse in host machines. But on the other side: Something had worked correctly with the installation: I have a process called vmware usr. But during the installation a text splashes that no X is found. (???) I’m realy a novice, but at this point under Breezy Badger vms usually I will be prompted to choose a resolution. What features do those of you see, who installed the tools under Drapper Drake? My tools installation only supports disk operations.
   
  Maybe opportunities to install the tools within a gnome console window and the features of changing resolution depend on the vmware tools version?
   
  * My vmware tools version: 19175.
   
  Regards Benjamin

---

