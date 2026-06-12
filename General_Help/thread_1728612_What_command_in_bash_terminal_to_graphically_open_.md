---
title: "?What command in bash terminal to graphically open a folder??"
date: 2011-04-13
forum: General Help
---

### Post by Tone303 on 2011-04-13
[COLOR=Blue]say your creating a .sh and you want to open a folder (graphically) with a command instead of pulling down the places menu and double clicking through folders. How do you do it? Is there a line that will open a folder? (GUI folder display, not change directory)[/COLOR]

Reason i ask this is because i cant get /dev/sda1 to open except if i go into system monitor, file systems tab and open there.

reason i ask is so i can create a panel shell button that will open that folder, this is another step in a project im doing, im devoloping the perfect emergency back up USB Booter. /dev/sda1 is your USB free storage space not part of the persistence virtual disk file free space, and the only other way to access it is through system monitor, file systems, it wont mount with disk mounter.

---

### Post by smithark on 2011-04-13
try the following anf then browse to the concerned folder:
"gksu nautilus"

---

### Post by Tone303 on 2011-04-14
> **smithark said:**
> try the following anf then browse to the concerned folder:
"gksu nautilus"

[COLOR=Blue]Reply:

Ok , thanks, the only thing missing from my emergency USB project is for people to easily access the real free space of their USB outside the persistence file; without using system monitor[/COLOR]

Trivial Chatter:

One way my emergency USB is customized is that it uses RAM Memory heavily, even for browsing the web, even for downloading videos that are hundreds of MegaBytes:

[http://f.imgtmp.com/JMTj4.png](http://f.imgtmp.com/JMTj4.png)

Other ways include top buttons that clear RAM memory, do cleanings, and more.

Ive been on my Emergency USB since march 15th, boot time is 53 seconds, speed is faster than hard drive after programs have been cached to RAM. USB activity is at 0% about over 99% of the time, regardless of browsing and other activities.

For some strange reason people think having 80% memory free and using 1/5th of your RAM you paid for is good. Like using 1/5th your CPU or 1/5th your food is good. Not on linux its not, this handles RAM perfectly even if you are 100% full of cache.

---

### Post by Tone303 on 2011-04-14
you know you cant know your Persistence File Free Space with the regular Disk Usage Analyzer? 

you have to actually make a top button script that does:

df -h -t aufs
sleep 5


theres all kinds of ways to make an emergency USB better that the USB-makers dont do. thinking if i could make a distribution for Emergency USBs.

I became interested in this after my hard drive physically broke and i started using one that i had put away in the drawer

---

