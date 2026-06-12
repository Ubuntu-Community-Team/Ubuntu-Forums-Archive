---
title: "Some positive reinforcement please"
date: 2010-02-14
forum: General Help
---

### Post by hankafyin on 2010-02-14
I finally have decided to give ubuntu a shot. Windows is becoming too familiar, and it's been forever since I have used command line since DOS. I really need some humility, and I think that Linux will teach me some. It was great to find this forum, I spent a couple hours reading posts and I am going to give it a whirl on a "spare" machine, dual booting with Windows 7 64 on two separate hard drives. I'm burning the ubuntu live cd x86 right now. I am going to unplug my windows drive and start the installation. Thanks again for the wonderful forum and a great source for information.

---

### Post by flippo on 2010-02-14
glad to hear your giving linux a shot, please just ask if you have any problems.

---

### Post by steveneddy on 2010-02-14
There is no reason to unplug the Windows drive.

Why do people think they have to do that? huh....

You may try using VirtualBox to install Ubuntu on while running Windows in case you make a mistake it is easier to correct and you don't mess up a HD accidentally lose data due to a lack of partitioning knowledge at first.

Also check out the links in my sig - I think they will help.

---

### Post by jken146 on 2010-02-14
Bear this in mind.  Windows wants to be installed first, and it wants to go on a primary partition at the beginning of the disk.  Install Windows first and Ubuntu second, and you should be just fine.  *Don't* unplug the drive with Windows on it; this will only confuse the bootloader and lead to problems starting one, the other or both OSs.

BTW, why the x86 CD? 64 bit linux works great!

---

### Post by 3rdalbum on 2010-02-14
DON'T unplug the Windows drive.

When you install Ubuntu, it will install the bootloader onto the first hard disk, and the bootloader will try to boot Ubuntu on the first hard disk in your case. When you plug the Windows drive back in, it may be that the Ubuntu drive is now the second hard disk, and you won't be able to boot Ubuntu.

If you keep the Windows drive plugged in, then Ubuntu will make sure that the bootloader can boot up Windows as well as Ubuntu.

---

### Post by hankafyin on 2010-02-15
I didn't want grub on my windows MBR, I would like to keep things separate. Is this the wrong way to do it. I have windows 7 64 bit installed already on a WD 500 GB Black, and I am installing ubuntu 9.10 on a WD 320 GB blue. I now that I need to edit the first.ist to dual boot and set boot piority in bios. Did I misunderstand something?
 
Here's my specs:
AMD Athlon II X2 245 Regor @3.480 (240X14.5) stock voltage 
AC Alpine 64 heatsink 
Gigabyte GA-MA785G-UD3H 
8GB (4x2) OCZ Blade DDR2 6400 2.0v 3:5 ratio 800 mhz 4-4-4-15 
WD Black 500 GB 7200 SATA 
WD Blue 320 GB 7200 SATA 
Avermedia Hybrid h788 TV tuner
PNY 9800 GT 1 GB (3 monitors) 
BFG 8800 GT OC2 (SLI unsupported)
CM Storm Scout Case

---

### Post by jken146 on 2010-02-15
It's more trouble than it's worth trying to keep GRUB off the MBR of the first hard disk. If you stick to the default options, things aren't likely to go wrong.

There's no messing around in the BIOS setup needed either.

---

### Post by hankafyin on 2010-02-15
Thank you for the heads up. I was ready to just dive in. I'm not concerned about losing data, this is a spare system that just has nothing on it but games for friends to use when they are over. Restarting ubuntu now. I assume all responsiblity for the state of this system. You won't hear me whinin'. Thank you for your help, I won't turn down advice, this is my first rodeo with Linux.
 
Installing drivers, things seem to be going well.  This is a learning experience for me, more fun than shootin' zombies.  Thanks again for all the help.

---

### Post by hankafyin on 2010-02-15
Here's one for ya....Why doesn't Window's windows wiggle.  Wiggling windows is cool!!!! I think I'm gonna like this Ubuntu thing. Thanks again all for your help.

---

### Post by jken146 on 2010-02-15
Haha! If you like that, install **compizconfig-settings-manager**, run **ccsm** and play with fire.

---

### Post by hankafyin on 2010-02-15
Thanks for bird doggin' some more fun!!  I think I better learn some basic commands first, and get to know the flow of the menus.  But I will sure give it a try.  I really wish I would have tried Ubuntu before I just spent $200 upgrading to Windows 7.  I will have to give the 64 bit a try too, after more trial and error and research.  It took my wife changing her major to Visual Technologies to give me the push to Linux, I can't have her gettin' smarter than me.  I wish you could see the grin on my face.  Lovin' it.

---

### Post by coldraven on 2010-02-15
After having installed various versions of Ubuntu/Kubuntu I have found the process to be usually quick and easy.
One little tip is that at about 80% of the install, usually when it says "Scanning mirror" the screen goes blank. After a brief panic I found that it was just the screensaver kicking in and pressing  an arrow key would wake it up. For some reason the default setting is to send the screen to sleep after 10 mins.

After dual booting for a year or so I finally deleted the Windoze partition and now run it in VirtualBox instead. :p

There is loads of info to be found but you could start here
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)


Have fun!

---

### Post by bowbalitic on 2010-02-15
If you like the wiggly windows you'll love the cube. Here's some pics of my system.
:) I don't know why buy I love to show it off... Sorry, I'm like a grandmother showing off her grandchildren :P


And that is a 3d moon revolving in the center of my cube.

---

### Post by coldraven on 2010-02-16
bowbalitic, that's nice! How do you get the Moon?
Must be awful being stuck in Ohio, I pine when I'm away from the ocean!

---

### Post by bowbalitic on 2010-02-16
Lol, yes it sucks. Especially with 24 inches of snow :P

Its actually really to set-up the moon or any other 3d model. The problem is that it tends to take quite a bit out of your system. I have quad core, 8 gb ram, and 4870 gpu with 2gb internal ram. I actually keep it off most of the time because it sucks resources (especially when you make it huge and rotating)

But any way, here's how. Install compiz plugins unsupported. Either through synaptic or 

sudo apt-get install compiz-fusion-plugins-unsupported

Then you download any .obj you want. here are some good ones

[http://forum.compiz.org/viewtopic.php?f=130&t=10113&p=76695&hilit=model#p76695](http://forum.compiz.org/viewtopic.php?f=130&t=10113&p=76695&hilit=model#p76695)
[http://doc.ubuntu-fr.org/tutoriel/personnalisation_cubemodel_wallpaper_dynamique_et_usplash#les_themes_cubemodel_pour_compiz](http://doc.ubuntu-fr.org/tutoriel/personnalisation_cubemodel_wallpaper_dynamique_et_usplash#les_themes_cubemodel_pour_compiz)

The second one has the moon.

Once you have your obj, go to compiz, effects, Cube 3D Models. 
Then create a new model. Then tweak the settings VERY SLOWLY (its VERY sensitive) to how you want it.

---

