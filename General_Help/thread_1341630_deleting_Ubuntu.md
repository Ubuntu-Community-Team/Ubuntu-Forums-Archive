---
title: "deleting Ubuntu"
date: 2009-11-29
forum: General Help
---

### Post by Steadyhndz on 2009-11-29
I just installed Ubuntu last night, got WoW installed, and I just don't like it.  Too much stuff to go through just to install 1 thing, tried installing drivers for my graphics card and sound card and it just did not want to cooperate.  

I have nothing but Ubuntu on here right now, I have Windows Pro on a dvd (ISO file).  Is there a way I can delete ubuntu and have my harddrive clean?  Or is there a way I can load Windows, then delete Ubuntu

---

### Post by fluffman86 on 2009-11-29
How were you trying to install your graphics drivers?  System > Administration > Hardware Drivers usually works wonders.  

Anyway, if you're dead set on going back to Windows, then just install Windows.  When it gets to the part about formatting a drive, just select your Ubuntu drive and do a quick format, and select it as the installation drive.

---

### Post by Steadyhndz on 2009-11-30
Yeah I'm going back to Windows.  There's just too much stuff to go through with ubuntu and that's because I don't know a lot about it.  2 of my friends convinced me to switch, and it's cool and all but Ubuntu wasn't made for gaming which is what I do mostly 

How could I load it, if it's an ISO?

---

### Post by fancypiper on 2009-11-30
> **Steadyhndz said:**
> I have Windows Pro on a dvd (ISO file).  Is there a way I can delete ubuntu and have my harddrive clean?  Or is there a way I can load Windows, then delete UbuntuHow did you manage to have a cd with an ISO file on it?  All Windows install CDs that I have owned are bootable.

BTW, an ISO is an image file.

[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804/EN-US/")

---

### Post by jrrader on 2009-11-30
Not that I'm trying to talk you into staying (I'm sure you could have figured out "put DVD in tray and install windows" on your own), but I play games on Ubuntu and they work beautifully.  The reason Windows is a "gaming platform" is because that's what all the commercial game software was written for.  Linux users are just less likely to spend money on games - so why write games for us?

Edit -
Right click on the iso  image and choose to burn it to disk to make it bootable.

---

### Post by Steadyhndz on 2009-11-30
> **jrrader said:**
> Not that I'm trying to talk you into staying (I'm sure you could have figured out "put DVD in tray and install windows" on your own), but I play games on Ubuntu and they work beautifully.  The reason Windows is a "gaming platform" is because that's what all the commercial game software was written for.  Linux users are just less likely to spend money on games - so why write games for us?

I wish games were programmed to work on linux, my game runs a little smoother, but everytime I reboot, I lose sound and I gotta do all this BS through alsa, it's just a hassle.  I'm just gonna put windows on and take care of it this time lol.  Before I had my harddrive almost full 200gb (only a 250gb harddrive)

I'm just going to put WoW, ventrilo, mozilla, itunes, AIM, and Yahoo messenger on my computer.  Not gonna screw it up this time

---

### Post by jrrader on 2009-11-30
> **fancypiper said:**
> How did you manage to have a cd with an ISO file on it?  All Windows install CDs that I have owned are bootable.


If you buy it as a download, or download it from a torrent, you will end up with an iso image.  Someone who didn't know how to properly burn an iso to disk must have given it to him.

---

### Post by jrrader on 2009-11-30
> **Steadyhndz said:**
> 
I'm just going to put WoW, ventrilo, mozilla, itunes, AIM, and Yahoo messenger on my computer.  Not gonna screw it up this time

[www.ccleaner.com](www.ccleaner.com)
[www.piriform.com/defraggler](www.piriform.com/defraggler)

These two keep windows running pretty smoothly.

---

### Post by Cytochromec on 2009-11-30
If gaming is your primary thing, then your better off in Windows anyway. Wine works, but its not gonna be as good as running Windows natively. 

To keep your windows from becoming a mess again, install Avira AV (free), CCleaner, and spybot search & destroy. You should also consider regularly defraging your drive. I dont know of any decent free ones, but disk keeper and others have set it and forget it options that defrag when your idle. Most important of all, avoid installing something unless its necessary, because uninstalling clutters that registry (no matter how you delete it or what reg cleaner you use). 

Also, you might want to consider partitioning your drive if you haven't, say 30gb for windows and the rest for your files. Then install windows, install your must have programs, create a OS image, and format regularly like most hardcore users. After a couple times, you'll get it down and a complete format will hardly take up time (hardly is relative, but since your a gamer, you must have a lot more).

---

### Post by wilee-nilee on 2009-11-30
I have a ISO from Digital River it was a student upgrade, I was lucky that at the time I downloaded it MS was providing a DVD/ISO to thumb so I have a DVD I bought and a bootable thumb with W7 pro to install with.

---

### Post by john newbuntu on 2009-11-30
Just install virtualbox (or VMware server) on ubuntu.  Now within the virtualbox environment, you can install windows and/or any version of linux/*nix.
This way, no uninstall/partitioning issues.  If you don't like your host OS, just go in to any of your guest OS.

---

### Post by Steadyhndz on 2009-12-01
Ok, I got virtualbox installed, and I have no idea how to use it lol

---

### Post by Primefalcon on 2009-12-01
> **Steadyhndz said:**
> Ok, I got virtualbox installed, and I have no idea how to use it lol
**stop**

while you still have Ubuntu installed just copy the ISO to your desktop, put in a blank cd/dvd and double click the iso file, just follow the prompts then, and you should have a bootable windows disk.....

just restart while having your new windows disk in drive, just select to wipe the partition and install windows, and you'll be back to a windows only enviro..

as said previously someone who didn't know how to burn iso's did it, Windows doesn't know how to urn ISO's without addon software

---

### Post by fluffman86 on 2009-12-01
You can't play games in VirtualBox anyway.  No 3D support.

---

### Post by Steadyhndz on 2009-12-01
> **Primefalcon said:**
> **stop**

while you still have Ubuntu installed just copy the ISO to your desktop, put in a blank cd/dvd and double click the iso file, just follow the prompts then, and you should have a bootable windows disk.....

just restart while having your new windows disk in drive, just select to wipe the partition and install windows, and you'll be back to a windows only enviro..

as said previously someone who didn't know how to burn iso's did it, Windows doesn't know how to urn ISO's without addon software


I'm gonna have to call my friend over for that... it says I can't mount it or w/e so i went on some other forums, some ppl were having the same problems, and I guess my version of Ubuntu (Hardy) won't run this or w/e.  I tried all the commands and everything that these guys are trying, and someone finally said that it doesn't work with the version I have
here's a link to the post

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/106910](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/106910)

When I put the cd in, i get this error Unable to mount the volume 'UDF Volume'

---

### Post by Steadyhndz on 2009-12-02
?

---

### Post by RJ12 on 2009-12-02
Well I wish you good luck with your Windows. If you want to stay with Ubuntu the new VMware Player 3 allows to create VMs and I think actually has 3d support.

If you download it all you have to do is go in the terminal, browse to the directory that you downloaded to and type "sudo sh whateverthefilenamewas.i386.bundle" without quotes (the .i386 and .bundle might be different). Once again good luck and make sure you have your product key.

To your answer on VirtualBox
Open virtualbox click on new and follow the prompts
Then mount the iso by clicking on settings and going to CD/DVD and there will be something about a iso and choose your iso file.
There is actually 3d support I think (its on the general tab)
Now click your VM and choose start!:o

---

### Post by Steadyhndz on 2009-12-03
I'm just gonna have my friend come over and do all of this crap for me, I downloaded the VMware player, but it won't fricking run... I did what my friend said and he even said he doesn't know what's goin on, so he's gonna come over and just wipe it.

---

