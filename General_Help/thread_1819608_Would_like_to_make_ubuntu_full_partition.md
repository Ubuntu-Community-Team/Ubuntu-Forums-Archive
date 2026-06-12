---
title: "Would like to make ubuntu full partition"
date: 2011-08-06
forum: General Help
---

### Post by Crazy K on 2011-08-06
Hey guys, I recently got a used computer a while back and I installed ubuntu 10.04 along with windows vista business which was installed before I got it. Windows vista is pretty much shot and I could care less for it. I'd like to make Ubuntu 10.04 to a full install and get rid of windows vista.

I can't seem to load the Ubuntu 10.04 installation DVD at startup. Whenever I start it up I can't seem to load it up. I just want to start over with a full copy of Ubuntu rather than a dual boot. How can I do that? Thanks!

---

### Post by jayadeep on 2011-08-06
please see that you have set the first boot pririty for DVD drive

---

### Post by Crazy K on 2011-08-06
how do I do that?

---

### Post by gizmo720 on 2011-08-06
When your computer turns on, before grub loads, see if it says how to get to the boot menu. On most computers this is f2, f8, or f12.

---

### Post by justinjthomas on 2011-08-06
> **Crazy K said:**
> how do I do that?

Set the boot device priority by changing it at the startup.

Look on the screen where the motherboard's name and logo comes up at the startup.

From there either select the boot options OR select the bios settings.

Then change the first boot device from Hard Disk to DVD Drive.

This will do the trick :)

---

### Post by linfidel on 2011-08-06
Basics:
BIOS *setup* sets the order of boot devices.  When your computer boots, the first thing it usually says is something like "Press F2 for setup", or for many desktops, the delete key.  You need to press this immediately; if you see it on the screen, and read what it says, it's probably too late, and you'll need to start over.

Once you get into the BIOS setup, you need to set the CD or DVD drive as the 1st boot device. If it doesn't find a bootable disk, it will continue on to boot the hard disk, so this setting can be permanent.

Questions about this are not anything to do with Ubuntu or any OS.  It's a general computer question, and you can find lots of info on how to do it.  GIYF.

---

### Post by enimeizoo on 2011-08-06
Why not just delete the windows partition (gparted would do it pretty easily), run update-grub and create an ext4 with the free space, or enlarge the current one?

---

### Post by Nithogger on 2011-08-06
> **enimeizoo said:**
> Why not just delete the windows partition (gparted would do it pretty easily), run update-grub and create an ext4 with the free space, or enlarge the current one?

My thoughts exactly. GParted works quite good, and is reliable. I have a special rescue CD with GParted on it. A friend of mine suggested it, because it's more reliable to remove and edit partitions from an external source. Like a CD or so. 
If you do it using windows or Ubuntu it's a bit like you live in Germany (for example) and you only know what happends in Germany, you don't know anything of Poland at all. Only that it's there. And yet, you have to tell how many people live in Poland. right? (I tried changing things on my HDD using ubuntu and Disk Utility and made a mess of my HDD this way) 

I'm not sure if you've got admin rights on the CD version of ubuntu, if not: look for something else. If so: you can use this here below: 

Get a CD with an OS on it, and GParted (I think you can install any version of Ubuntu on the CD to use GParted but i'll come back on that later). Then, restart your computer once you've got Ubuntu installed on the cd and get into the BIOS, change the boot sequence and restart it. Make sure the boot priority is set to the DVD reader first (or Flashdrive port if you're using a flashdrive, which I would recommend though since you've got more space on a flashdrive). Choose to go to ubuntu desktop. After you've checked you have internet connection and internet access start Terminal (ctrl + alt +t ) and type: Sudo apt-get install gparted (no caps). Hit enter a couple of times. and install it. run it and resize your partition. follow all the steps etc. and you're done.
Since gparted edits system things. It's located in the System/Administrator map. Just so you know it's there and not in the applications menu ;)

---

### Post by linfidel on 2011-08-06
> **Nithogger said:**
> My thoughts exactly. GParted works quite good, and is reliable. I have a special rescue CD with GParted on it. A friend of mine suggested it, because it's more reliable to remove and edit partitions from an external source. Like a CD or so. 
If you do it using windows or Ubuntu it's a bit like you live in Germany (for example) and you only know what happends in Germany, you don't know anything of Poland at all. Only that it's there. And yet, you have to tell how many people live in Poland. right? (I tried changing things on my HDD using ubuntu and Disk Utility and made a mess of my HDD this way) 

I'm not sure if you've got admin rights on the CD version of ubuntu, if not: look for something else. If so: you can use this here below: 

Get a CD with an OS on it, and GParted (I think you can install any version of Ubuntu on the CD to use GParted but i'll come back on that later). Then, restart your computer once you've got Ubuntu installed on the cd and get into the BIOS, change the boot sequence and restart it. Make sure the boot priority is set to the DVD reader first (or Flashdrive port if you're using a flashdrive, which I would recommend though since you've got more space on a flashdrive). Choose to go to ubuntu desktop. After you've checked you have internet connection and internet access start Terminal (ctrl + alt +t ) and type: Sudo apt-get install gparted (no caps). Hit enter a couple of times. and install it. run it and resize your partition. follow all the steps etc. and you're done.
Since gparted edits system things. It's located in the System/Administrator map. Just so you know it's there and not in the applications menu ;)
How do you run a rescue CD if you can't boot from the CD Drive?

But yes, if you can boot a live CD, you can run gparted from that, with no problem.  Not sure what you are talking about with installing gparted - do you know a way to install a program on a CD?  No matter though, it's already there.

---

### Post by enimeizoo on 2011-08-06
That is wrong, you can perfectly use gparted from your current installation to get rid of windows. You only will have a problem if you really want to enlarge your partition instead of creating another ext4. 
Actually, it is safer, since this way you can't harm the mounted drives (eg : your ubuntu install)

To do that, you don't need to boot from a CD. However, booting from a cd can be really useful, and you might want to solve the boot problem once you have solved your OS issue. You could choose to solve the booting issue first, though, but I'd advice to do one thing at a time, whatever you choose.

---

### Post by Crazy K on 2011-08-08
I was able to get into BIOS. I was having problems getting into it, but finally got into it. And I was able to make it into a full install. 

But I'm having a weird problem at startup. Whenever I start up, it sticks on a dark screen with a white underline blinking for a minute or two. When I had windows installed alongside it, Ubuntu started up in nearly seconds. 

It's not a huge problem though.

---

