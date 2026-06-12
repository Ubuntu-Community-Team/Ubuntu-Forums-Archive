---
title: "how much swap do i need?"
date: 2010-10-28
forum: General Help
---

### Post by 5PUTN|K on 2010-10-28
i got a 500 gb hard drive and i made 3 partions on it 10gb for swap 410gb for ubuntu 10.10 64bit and 80gb win7 and i set the swappiness to 10 but the system monitor shows that no swap space is being used at all [http://img32.imageshack.us/i/screenshotkcr.png/](http://img32.imageshack.us/i/screenshotkcr.png/) do i need to resize my swap partion or change theswappiness value? i thought i needed 2.5*ram swap space but i guess i got it wrong 

[IMG]http://img32.imageshack.us/f/screenshotkcr.png/[/IMG]
[IMG]http://img32.imageshack.us/f/screenshotkcr.png/[/IMG]

---

### Post by matt_symes on 2010-10-28
Hi

How much memory do you have? I want at least the amount of memory you have + a bit more for hibernation (which also uses swap).

Kind regards

---

### Post by yetiman64 on 2010-10-28
> **5PUTN|K said:**
> i got a 500 gb hard drive and i made 3 partions on it 10gb for swap 410gb for ubuntu 10.10 64bit and 80gb win7 and i set the swappiness to 10 but the system monitor shows that no swap space is being used at all do i need to resize my swap partion or change theswappiness value?

[IMG]http://img32.imageshack.us/f/screenshotkcr.png/[/IMG]
[IMG]http://img32.imageshack.us/f/screenshotkcr.png/[/IMG]

How much RAM do you have ? And do you plan to use hibernation ?
Also what is the "swapiness" setting you mention and how is it set ?

---

### Post by gstilma on 2010-10-28
You will never use that much swap. Everything I've read says that swap doesn't need to be more than 2x RAM, but as you see, that's even playing it safe. I've only got 1.3GB RAM and I set swap to 3GB, but I've almost never needed any of it.

---

### Post by 5PUTN|K on 2010-10-28
ive got 4 gb ram so i thought i should have 10 gb swap  i kinda use hibernation alot and sometimes i just lock the screen and download torrents all night [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) and thats where i learned about swappiness

---

### Post by yetiman64 on 2010-10-28
> **5PUTN|K said:**
> ive got 4 gb ram so i thought i should have 10 gb swap

If you plan to use hibernate then as matt_symes suggested a little bit more than that (5 GB would probably suit).

If you don't plan to hibernate probably 1.5 or 2 GB would be enough. 

The figure of 1.5 to 2 times RAM is old information (suitable for smaller RAM machines) and this much is a bit of a waste of HDD space on larger RAM machines, as you have noted swap is rarely used due to the size of the memory you have installed.

Edit: that is interesting information about swapiness values, I will have to look further into that for my own use, thanks.

---

### Post by 5PUTN|K on 2010-10-28
thanks for the help so ill have to reinstall ubuntu and make a 5 gb swap partion this time and i was also wondering does the order in which i create the partions effect performance at all i mean i put the swap space at the beginning in dev sda 1 ubuntu in dev sda2 and windows in dev sda3 i thought swap was the most used partion so it would be quicker if it were there but since its not used that much i can put it on dev sda2 and ubuntu in dev sda1 so that ubuntu will be faster right?? or am i just making this up?? i mean that little head doses the reading and writing so it has to move a lot more to get to the ubuntu partion now doesnt it? if i put ubuntu at the beggining that partion is placed in the midle of the disk right?

---

### Post by yetiman64 on 2010-10-28
It is possible to resize partitions (shrink swap and expand Ubuntu) from a live cd with gparted, however if you do this full data backups are recommended (for the whole drive) and it is not recommended to do such if Windows partitions are involved (Use Windows tools on Windows partitions if they are). Just remember to set "swapoff" in gparted if you go this way.

If you can't unmount all partitions or turn swapoff with the Ubuntu live cd, then the gparted live cd available from _[--here--]("http://gparted.sourceforge.net/download.php")_ (stable version is best) can be used. Just download the .iso and burn a cd if needed.

Edit: not sure if it makes that much difference where the swap is located, but just to note, I have a 10 GB swap (for 8 GB RAM) at the very end of the drive (sda3 in my case) and it works OK.

---

### Post by dcstar on 2010-10-29
Please - all of you - read this before sprouting invalid opinions about swap:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Grenage on 2010-10-29
> **dcstar said:**
> Please - all of you - read this before sprouting invalid opinions about swap:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Can you have an invalid *opinion*? ;) (it was also already linked above).

Considering that you use hibernation, I would use 5GB.

---

