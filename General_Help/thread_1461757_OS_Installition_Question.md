---
title: "OS Installition Question"
date: 2010-04-24
forum: General Help
---

### Post by physic.dude on 2010-04-24
[COLOR=black][FONT=Verdana]Ok, on my computer I started with Windows XP, later I decided to duel boot it with ubuntu. Now I recently got Windows 7 and would now like to tri boot.  I currently have 3 HHD's in my computer, 1 for ubuntu, 1 for XP and 1 blank one that I will install Windows 7 on. My question is, will the GRUB boot loader see Windows 7 on the list after I am done installing it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Current ubuntu is 9.10[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by mikewhatever on 2010-04-24
No. Installing W7 doesn't tell Grub it got installed. Try running **sudo update-grub** when done, and if that doesn't work, a manual entry for W7 may do.

---

### Post by physic.dude on 2010-04-24
[COLOR=black][FONT=Verdana]After I finish will my computer go directly to W7 or GRUB? If it goes to GRUB then how do I get to W7, or if it goes to W7 then how do I get to ubuntu?[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by lukeiamyourfather on 2010-04-24
> **physic.dude said:**
> [COLOR=black][FONT=Verdana]After I finish will my computer go directly to W7 or GRUB? If it goes to GRUB then how do I get to W7, or if it goes to W7 then how do I get to ubuntu?[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

Someone correct me if I'm wrong but Windows will install its own boot loader on the disk chosen during installation. If this happens to be the same disk Linux is on it will overwrite GRUB and GRUB will have to be installed again. In your case since it will be on a different disk you just need to add the Windows installation to GRUB when you're done installing Windows.

Alternatively you can use the native boot loader on each disk for the given operating system and select the boot disk with the BIOS (usually push F10 or similar to get boot device selection list during POST). This is handy if you don't want the installations dependent upon one another for booting or if you change hard disks or operating systems often. Cheers!

---

### Post by physic.dude on 2010-04-24
> **lukeiamyourfather said:**
> Someone correct me if I'm wrong but Windows will install its own boot loader on the disk chosen during installation. If this happens to be the same disk Linux is on it will overwrite GRUB and GRUB will have to be installed again. In your case since it will be on a different disk you just need to add the Windows installation to GRUB when you're done installing Windows.
 
Alternatively you can use the native boot loader on each disk for the given operating system and select the boot disk with the BIOS (usually push F10 or similar to get boot device selection list during POST). This is handy if you don't want the installations dependent upon one another for booting or if you change hard disks or operating systems often. Cheers!
 
 
Well I will be using [COLOR=black][FONT=Verdana]separate HHD's. And I do tend to switch OS's frequently.[/FONT][/COLOR]

---

### Post by physic.dude on 2010-04-25
Never mind everyone, W7 just slapped slapped me with a big smelly tuna fish. :?

I am pleased to announce that i will now be a 100% Ubuntu user. \\:D/

When I installed W7 and selected the newest HDD to install it on, W7 had some crazy boot loader of its own and made it completely impossible to start Ubuntu. Even if the Ubuntu HHD was the only one in the computer it wouldn't start. and Windows XP was a hassle to get running to back up my files. In the end I had to reinstall Ubuntu as the only OS. I keep my old Windows XP drive here just in case I need to get more of my files off it. 

I'm ok with it anyway. 
[BUT if i cant get my Steam games working then I'm gonna be]("http://ubuntuforums.org/showthread.php?t=1462423") :evil: :evil: :evil: 
^^^click that^^^

---

