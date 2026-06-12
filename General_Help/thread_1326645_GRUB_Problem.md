---
title: "GRUB Problem"
date: 2009-11-14
forum: General Help
---

### Post by eigurrola on 2009-11-14
hello everyone,
 I'm new to this Ubuntu world, just installed it one week ago, but I have been having trouble with the GRUB booter here's my story, thanks in advance for taking your time to read it.

I've been using Windows Vista in my laptop, but recently a friend of mine told me it would be nice to have Ubuntu in there as well, I had heard many things about it so I did

I downloaded Ubuntu 9.10 and I recently had bought a new external USB hard drive. So I made a partition on that hard drive and installed Ubuntu in there. It installed pretty good and so far I've been amazed at what Linux can do, however, I'm still a newby to the OS and I still need Windows Vista to do a couple of things for school (I don't really have much time to experiment and do the homework at the same time)

So here's the problem:
Whenever I turn on the laptop I get this display
"GRUB loading."
it takes about a minute and then two things can occur:

1:If the hard drive is connected to the USB terminal it loads fine (at least at the second-third try) and brings up the menu where I can select which OS to use.

2.If the hard drive is unplugged, it pops a message 
"Error, files not found
 GRUB Rescue >" 
and it lets me type in a command, similar to the terminal.

The quickest solution is to have the hard drive connected... however, since I'm using a laptop it's not cool to be having to carry the hard drive around, especially since it needs an external power supply... 

So basically I wanted to know if it's possible to install the GRUB booter in my laptop's internal hard drive and having it run from there without the need of having to connect the external one (obviously I would be using Vista at that time and plug in the external drive whenever I'm using Ubuntu) or simply a way of bypassing it and starting Vista I would not mind having to type in a command or something

By the way, the GRUB version is 1.97 beta 4.

Thanks for the help, in the meanwhile I'll keep looking for an answer in the documentations.

---

### Post by mikewhatever on 2009-11-14
Yes, the way to solve it is to restore the Vista boot loader first, and then reinstall grub.[How to reinstall GRUB]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

The howto assumes that Grub is going to be installed to the MBR of the first hard disk, which is the way you have it now. Therefore, you'd need to change /dev/sda to /dev/sdb or /dev/sdc, whatever the designation of you external disk is. Rub **sudo fdisk -l** to find out.

---

### Post by eigurrola on 2009-11-15
Thank you very much, 
although the link is kind of weird but I searched for it and found some usefull information thank you

---

### Post by mikewhatever on 2009-11-16
Fixed the link above. ;)

---

