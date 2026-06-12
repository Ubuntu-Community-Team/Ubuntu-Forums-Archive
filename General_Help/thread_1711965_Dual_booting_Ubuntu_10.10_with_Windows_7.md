---
title: "Dual booting Ubuntu 10.10 with Windows 7"
date: 2011-03-22
forum: General Help
---

### Post by RandomNoob87 on 2011-03-22
Hey guys.
So tonight I was trying to install Ubuntu 10.10 on a partition on my hard drive (640gb. 60gb partition made for Ubuntu) and when I got to the part of the installation (was able to successfully boot ubuntu through a usb) where you allocate which partition you are going install Ubuntu ON i selected the 60gb partition I had made and when I hit install it told me "No root file system is defined. Please correct this from the partitioning menu". What does it mean by "root file system"? I've had no experience with Ubuntu or any Linux OS before this but desperately want to learn how to use it. One thing that I'm concerned about is that if my computer not being connected to the internet (dont have any at my house at the moment) is causing certain issues in the installation? obviously that wouldnt affect the root file system problem im having but when I selected my time zone it was trying to connect to something which im sure needed an internet connection. 
I have ordered a Ubuntu 10.10 install cd from the Ubuntu website but it will take a few weeks to get here so in the meantime im trying to see if I can install it via a bootable usb just for kicks/experience. Can't use a cd/dvd with ubuntu burned onto it because my dvd drive is a bit messed up.
Here's a photo of when it says "No root file system is defined. Please correct this from the partitioning menu".
[http://img847.imageshack.us/img847/6311/norootfilesystemdefined.jpg](http://img847.imageshack.us/img847/6311/norootfilesystemdefined.jpg)
Sorry for the sporadic post. I have to go to my dads business in order to use the internet until i get internet at my place or get a laptop so posting new photos of whatever it is that some of you might request isnt easy. Hopefully you can help me, would love to finally be able to learn all about Ubuntu.

---

### Post by An Sanct on 2011-03-22
Did you format the 60Gb with NTFS? (It's important, so that my advice will not harm your previous windows installation)

---

### Post by RandomNoob87 on 2011-03-22
:shock: Yeah turns out that plus something else stopped it from installing correctly!
I also forgot to create the swap partition drive so I did that and it worked better. Now the problem is that when I get to the last step of the installation it asks for my name and username (same thing) 
here's a photo of it.
[http://bit.ly/hcW3XH](http://bit.ly/hcW3XH)
here's the youtube tutorial that I used.
[http://www.youtube.com/watch?v=FmN4Pj3VWpc](http://www.youtube.com/watch?v=FmN4Pj3VWpc)
The mistake I made beforehand was that I used a tutorial for ubuntu 10.04 and didnt bother to look for a 10.10 tutorial or really realize that it said 10.04 at first...
anyways I'm wondering why it wont let me go pass that last step :confused:

---

### Post by Script Warlock on 2011-03-22
could it be your user settings thats why it stalled, green check means your good to go.

---

### Post by RandomNoob87 on 2011-03-22
Well i cant connect to the internet from that computer at this time so you think just because im not connected to the internet its not letting me finish the installation?
pretty lame. Ubuntu's whole advertising theme is that its a very simple OS to use. 
Anyways i probably can find a way to connect to the internet on it so hopefully that solves this. Also I had realized that I hadnt formatted the bootable usb I was using in NTSF form (was fat32) and I did that right now. THEN when I tried to bootup ubuntu in BIOS it just said "BOOTMGR IS MISSING. PRESS CTRL+ALT+DELETE TO RESTART".
So now I reformatted my usb through the command line (cmd) and made it bootable again with unetbootin and hoping that it works this time. :roll:

---

### Post by wilee-nilee on 2011-03-22
In the custom install new partition where the pop up lets you actually activate the partition is another drop down below that and in the line above that drop down you need this /  that is root.

Your failure has nothing to do with a swap or being on line or the OS.

---

### Post by cookiecloud on 2011-03-22
I'm sorry to sound pedantic and fussy, OP, but could you please consider formatting your posts in a slightly more readable way? It helps greatly, and will encourage people to help you faster, if they don't get "visual indigestion".

I don't want to sound mean, but it is just a wall of text, and my brain kinda groaned at my eyes.

CC

---

### Post by RandomNoob87 on 2011-03-27
> **wilee-nilee said:**
> In the custom install new partition where the pop up lets you actually activate the partition is another drop down below that and in the line above that drop down you need this /  that is root.

Your failure has nothing to do with a swap or being on line or the OS.


oh ok
thanks ill try that and post results

sorry ive been kind of busy the last week or so #-o

---

### Post by RandomNoob87 on 2011-03-27
> **cookiecloud said:**
> I'm sorry to sound pedantic and fussy, OP, but could you please consider formatting your posts in a slightly more readable way? It helps greatly, and will encourage people to help you faster, if they don't get "visual indigestion".

I don't want to sound mean, but it is just a wall of text, and my brain kinda groaned at my eyes.

CC

its the internet

I dont need to write with iambic pentameter and **** like that.
Its not a essay.:lolflag::rolleyes::cool:<--umad

---

