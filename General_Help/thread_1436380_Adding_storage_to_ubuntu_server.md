---
title: "Adding storage to ubuntu server"
date: 2010-03-22
forum: General Help
---

### Post by Eatingamazon on 2010-03-22
[COLOR=black][FONT=Arial]I was running a fedora file server before I found out that Windows home server would let you pool your hard drives no matter what size they were and show it as one data drive i had lots of old drives lying around so this was a perfect way to use them. I downloaded the trial version and have been using it for about 18 month (two installs) But Microsoft have stopped their 6 month trial and are now only offering a 30 day trial. My Question is does Ubuntu offer the same feature and is it easy to set up.[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]Would also like to add I have recently nervously installed ubuntu net book on a friend’s Net book. I say nervously because my last few encounters with Linux (Fedora) have been difficult but I was very impressed with the system allot easier to use and I am thinking of setting up an Edubuntu pc for my Kids to use.[/FONT][/COLOR]

---

### Post by bodhi.zazen on 2010-03-22
First, if you are wanting to run a file server, I advise Centos rather then Fedora.

The feature I believe you want is LVM :

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

LVM works in Ubuntu, as well as Centos or Fedora, you need to use the Alternate CD with manual partitioning.

Be warned, the only "problem" with these things is that if one drive fails you can loose data. Sure there are recovery tools, but they do not always work.

One question, are you sure you need this feature ?

---

### Post by Eatingamazon on 2010-03-23
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]The Drives I have are 145, 250, 500, 750*2  I am not an expert just know how to use computers from trying things and find they work or usually do not work. I do not think you can use raid to join the drives to appear as one drive because they are different sizes. If you can that is great. Or if there is another way please let me know. I back up to a 1500 external drive so not to worried about drive failures[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by bodhi.zazen on 2010-03-23
> **Eatingamazon said:**
> [COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]The Drives I have are 145, 250, 500, 750*2  I am not an expert just know how to use computers from trying things and find they work or usually do not work. I do not think you can use raid to join the drives to appear as one drive because they are different sizes. If you can that is great. Or if there is another way please let me know. I back up to a 1500 external drive so not to worried about drive failures[/FONT][/COLOR]
[/FONT][/COLOR]

Not RAID, LVM, see the link I gave you.

---

