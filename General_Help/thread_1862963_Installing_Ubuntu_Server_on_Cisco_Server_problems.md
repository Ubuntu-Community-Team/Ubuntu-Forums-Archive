---
title: "Installing Ubuntu Server on Cisco Server problems"
date: 2011-10-17
forum: General Help
---

### Post by WarrenSullivan on 2011-10-17
Hi guys, 
New to the forum and new to ubuntu, i am a noob, i said it!!! 
Im a Cisco guy and i have grabbed a cheap Cisco MCS 7835H-1 server off ebay for dirt cheap,its for study, i want to eventually use it as my TFTP, RADIUS, and GNS3 platform, for this i have chosen ubuntu, but im running into a few problems and dont really know where to go from here, i downloaded ubuntu server 8.04-4 and burnt it on a disk, rebooted the server and installed it, all went well until i rebooted to run ubuntu......no luck, it states....
Error 21: Selected disk does not exist

Press any key to continue...

i read somewhere about getting a boot output but have no idea how to do it?

Any help will be really appreciated!

Thanks heaps in advance,

PS im not here to get one problem resolved and the take off, i want to really get to know Ubuntu, looks the goods!

---

### Post by WarrenSullivan on 2011-10-17
also i read [here]("http://www.tomshardware.com/forum/236544-50-ubuntu-doesn-load-install") about a very similar problem, but i don't really understand half of what they are saying!!! lol

---

### Post by collisionystm on 2011-10-17
> **WarrenSullivan said:**
> Hi guys, 
New to the forum and new to ubuntu, i am a noob, i said it!!! 
Im a Cisco guy and i have grabbed a cheap Cisco MCS 7835H-1 server off ebay for dirt cheap,its for study, i want to eventually use it as my TFTP, RADIUS, and GNS3 platform, for this i have chosen ubuntu, but im running into a few problems and dont really know where to go from here, i downloaded ubuntu server 8.04-4 and burnt it on a disk, rebooted the server and installed it, all went well until i rebooted to run ubuntu......no luck, it states....
Error 21: Selected disk does not exist

Press any key to continue...

i read somewhere about getting a boot output but have no idea how to do it?

Any help will be really appreciated!

Thanks heaps in advance,

PS im not here to get one problem resolved and the take off, i want to really get to know Ubuntu, looks the goods!

First, dont use Hardy Heron ubuntu server 8.04-4. Use 10.04

Second, it sounds like your server is set to boot from the CD. you need to change you boot options in the bios to boot from the hard drive.

---

### Post by WarrenSullivan on 2011-10-17
Its booting from the harddrive, i have changed it in boot options, the DVD drive has no cd in it anyway...i ran the repair broken install thing and managed to change the drive from (hd1,0) to (hd0,0) and i can boot the grub i believe? i have to log on to it, its like a command line interface.....

---

### Post by WarrenSullivan on 2011-10-17
oh my god, it doesn't have a gui.....i just realized this, ill install the desktop edition lol sorry for the inconvenience 

pffft no gui, you'd think because im a cisco guy id like no gui.....i don't lol

---

### Post by collisionystm on 2011-10-17
> **WarrenSullivan said:**
> oh my god, it doesn't have a gui.....i just realized this, ill install the desktop edition lol sorry for the inconvenience 

pffft no gui, you'd think because im a cisco guy id like no gui.....i don't lol

Don't use the desktop edition on a server.. you will regret it because it is slow as hell when it comes to server tasks.

What are you planning on using the server for?? If you want a GUI and want to learn Linux without taking a week to put the box together, check out Zentyal. Its absolutely the best thing out there right now and its based on Ubuntu 10.04. I use it at my company.

---

