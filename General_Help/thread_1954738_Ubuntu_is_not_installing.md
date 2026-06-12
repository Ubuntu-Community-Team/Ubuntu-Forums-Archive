---
title: "Ubuntu is not installing"
date: 2012-04-08
forum: General Help
---

### Post by camshot on 2012-04-08
Hey guys,
Actually im trying to install Ubuntu onto my Hard Drive as second systen, everything worked fine until I had to restart, it booted normally up and tried to finish the installation but its just hanging up, but it is showing it to me when i put things out and in and I can type things...
I made a video showing the Problem:
[B]
[http://www.youtube.com/watch?v=wTC8__TPU4c](http://www.youtube.com/watch?v=wTC8__TPU4c)[/B]

It happens with the **64Bit version and with the 32Bit version**...

[B]

Here is my System:[/B]

Motherboard 
ASUSTeK Computer INC. P8P67 REV 3.1 (LGA1155) 

Graphics Card
1280MB GeForce GTX 570 

Ram 
8,00 GB Dual-Kanal DDR3 @ 668MHz (9-9-9-24) 

CPU 
Intel Core i7 2600K  @ 3.40GHz 

Hard Drive
117GB OCZ-VERTEX3 (SATA) 


I hope you can help me and if you need some more Information I can post them.
-Thanks

---

### Post by camshot on 2012-04-08
Really no one got an idea? :???:

---

### Post by cody1233 on 2012-04-08
Sounds like you used Wubi to install from inside Win?  If yes, usethe liveCD installation.

---

### Post by Basher101 on 2012-04-08
it is the wubi installation from what i can see. Also, Ubuntu runs fine with the setup (you will only have to install the nVidia drivers for the card manually) i have pretty much the same stuff as you do.. if you want i can even explain it in german (will check the code of conduct meanwhile if i am allowed to..i will write the stuff down in english for now)

so to actually install it, 
1. delete wubi from your windows.
2. use the universal USB installer to make a bootable live-USB download here [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
3. select the usb drive to boot first in your BIOS
4. select run ubuntu (not install)
5. when you get to the desktop screen launch Gparted and make the partitions (you can make it an automatic install or make custom partitions. For the automatic install you just got to have a ~50 GB partition that is unallocated and then you launch the installer that is the only icon on you desktop)
6. Launch the installer and choose "install beside windows" for the automatic install, or "other option" for the custom partitioning
7. if you chose the custom method, you will need to assign the moint point "/" to the partition you want Ubuntu on. You will not need a SWAP partition as 8 GB RAM will be more than enough.

---

### Post by camshot on 2012-04-09
So I recorded everything from installing Ubuntu to the part where it stops.
In a few minutes it will be on YouTube...

Oh and can i write in German too or is this a ONLY Engish forum?

---

### Post by Basher101 on 2012-04-09
> **camshot said:**
> So I recorded everything from installing Ubuntu to the part where it stops.
In a few minutes it will be on YouTube...

Oh and can i write in German too or is this a ONLY Engish forum?

> write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries that visit here and English is the common language of these forums.

English only from what i see in the code of conduct

---

### Post by camshot on 2012-04-09
Okay so I uploaded the video to YouTube

--> [http://youtu.be/gLG6L0NUvQI](http://youtu.be/gLG6L0NUvQI)

---

### Post by Basher101 on 2012-04-09
something is certainly off...from what i see there are 2 things that come to my mind:

1.In the video it starts hanging at partitions (sdb and when it comes to sdc it hangs) my guess is that it is the Truecrypt (saw the icon on your desktop) you have on the parititons that gives it errors. Try to disconnect your hard drive, boot the USB and plug it back in if you came any further.

2. you could try to burn the .iso to a DVD and install it using the optical drive (will be alooooot slower but should work)

edit: after taking yet another look i am pretty sure that your truecrypt is hanging the boot sequence when the drivers try to read all storage devices but cant. Try option 1 to bypass this hangig and see if you can get to the desktop screen.

---

### Post by camshot on 2012-04-09
Hmm i now plugged out the ssd but its the same...
And if it is the usb i only got an app on my ipod wich allows me use use my ipod as an normal usb stick.. I can try it and will post later but i have to go for now...

---

### Post by Basher101 on 2012-04-09
try using an actual usb stick not an iPod. Or burn a DVD.

i guess that USB stick feature the iPod comes with is for storage purposes. I doubt that it was within the concept to be able to boot an Operating System with it.

---

### Post by camshot on 2012-04-09
This feature comes with a Jailbreak-App but I used an actual USB stick... I can try it from a DVD but the Drive is external... 
I will post it if it worked or not...

---

### Post by camshot on 2012-04-09
Still not working and I dis attached my SSD because of TrueCrypt

---

