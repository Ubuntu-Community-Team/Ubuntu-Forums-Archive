---
title: "Terrible perfomance... please help!"
date: 2010-08-18
forum: General Help
---

### Post by brianconnoly on 2010-08-18
Hi there!

My specs are:
Motherboard - MSI H55M-P31(MS-7636)
CPU - Intel(R) Core(TM) i3 CPU 530 @ 2.93GHz
RAM - 2Gb
GPU - ATI RadeonHD 5700 series (not sure.... but definetely ATI)

I have Ubuntu 10.04 x64 installed.

I noticed that Xorg loads CPU on 60%.

I work with 4 workspaces, I use LAMPP, Chrome(5-10 tabs), Geany(5-15 tabs), Nautilus(3-5 tabs) and a pidgin.

So.... please help me increase perfomance of system!
I love my ubuntu very much and don't want to leave it.

PS: I'm russian. So don't kick my *** for my english )))

---

### Post by sydbat on 2010-08-18
> **brianconnoly said:**
> Hi there!

My specs are:
Motherboard - MSI H55M-P31(MS-7636)
CPU - Intel(R) Core(TM) i3 CPU 530 @ 2.93GHz
RAM - 2Gb
GPU - ATI RadeonHD 5700 series (not sure.... but definetely ATI)

I have Ubuntu 10.04 x64 installed.

I noticed that Xorg loads CPU on 60%.

I work with 4 workspaces, I use LAMPP, Chrome(5-10 tabs), Geany(5-15 tabs), Nautilus(3-5 tabs) and a pidgin.

So.... please help me increase perfomance of system!
I love my ubuntu very much and don't want to leave it.

PS: I'm russian. So don't kick my *** for my english )))
My best guess would be that it has everything to do with the ATI card.

Are you running the proprietary ATI video drivers or the [open driver]("https://help.ubuntu.com/community/RadeonDriver")?

---

### Post by brianconnoly on 2010-08-18
I use proprietary driver.

---

### Post by sydbat on 2010-08-18
> **brianconnoly said:**
> I use proprietary driver.Perhaps give the open drivers a try and see if that works for you. They might be just as good, if not better, for your particular card.

---

### Post by brianconnoly on 2010-08-18
Thanks for advise.
Gone trying....

---

### Post by brianconnoly on 2010-08-18
hmm.... 

$ lspci -nn | grep VGA

ATI Technologies Inc Device [1002:68be] - is that my video card?

How can I determine real name?

---

### Post by sydbat on 2010-08-18
> **brianconnoly said:**
> hmm.... 

$ lspci -nn | grep VGA

ATI Technologies Inc Device [1002:68be] - is that my video card?

How can I determine real name?Get rid of the -nn option.

---

### Post by brianconnoly on 2010-08-18
now it's 
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68be

---

### Post by sydbat on 2010-08-18
> **brianconnoly said:**
> now it's 
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68beLooks right.

Another question - do you have 'Desktop Effects' enabled? If so, turn them off (System > Preferences > Appearance) and see if that speeds things up.

---

### Post by LowSky on 2010-08-18
buy more RAM... I suggest asnother 2GB of RAM and it isnt the graphics card driver. your system is trying to handle a lot of work at one time, and the core i3 is only a dual-core so you can only multitask so much. If you need more perfomance upgrade i5 or i7

---

### Post by brianconnoly on 2010-08-18
But I need effects!
I can't work without expose and scale....

---

### Post by brianconnoly on 2010-08-18
It became even worse....

---

### Post by brianconnoly on 2010-08-18
I can't buy anything because it's my work PC.

Is there any possibility to make my configuration work well?

---

### Post by sydbat on 2010-08-18
> **LowSky said:**
> buy more RAM... I suggest asnother 2GB of RAM and it isnt the graphics card driver. your system is trying to handle a lot of work at one time, and the core i3 is only a dual-core so you can only multitask so much. If you need more perfomance upgrade i5 or i7Upon re-reading the OP, I have to agree - more RAM. Because the OP is running so many things all at once, he is experiencing a system-wide slowdown.

Therefore, if the OP cannot upgrade to more RAM, yet> But I need effects!
I can't work without expose and scale....then I suggest running fewer applications at any given time until/unless more RAM is installed/deciding to turn off desktop effects.

---

### Post by Vrroom on 2010-08-18
Your swappiness may be high....reduce it to 10

---

### Post by brianconnoly on 2010-11-24
Upgraded to 10.10
All problems gone. Thnx!

---

### Post by dcstar on 2010-11-25
> **brianconnoly said:**
> Upgraded to 10.10
All problems gone. Thnx!

The it is **Solved** (read below).

---

