---
title: "my operating system complex"
date: 2011-09-13
forum: General Help
---

### Post by dan0804smith on 2011-09-13
so i used to have ubuntu hardy on my dell netbook (duel 1.6ghz~1gbram~160gb).  my problem with ubuntu is that the os would take up half of the ram and the cache would take up the rest.  this resulted in slow performance. so i switched to lubuntu natty.  its alright... i always have at least 250mb of spare ram  space.  its just that natty is a way to light for me.  so.  a change needs to be made.

these are my options:

1.bear with lubuntu.

2.  get a better os that is similar to ubuntu but wont devour my ram

3.  get ubuntu natty and set up a swap partition 

4.   spend 30$  bucks on a 2gb ram card,  sell my 1gb for $10-$15
  what are your thoughts?  i ahve never used a swap partition but im pretty sure it tears up your hardrive due to all of the frequent reading writing.  what are your thoughts on this?

---

### Post by Dangertux on 2011-09-13
I don't think that swap really puts that much extra wear and tear on your hard drive. Sure if you're constantly swapping out maybe. I really don't think so though. It's really no different then virtual memory in Windows though.

As far as if you should upgrade or not, if you have the means to I am sure the upgrade would give you noticeably better performance.

Instead of upgrading, have you considered using 10.04 LTS? I used it on a laptop that was way worse then what you have

Celeron 1.4 Ghz 512 MB RAM, 32 MB shared with integrated video (intel i855 to boot). It actually worked quite well out of box with no extra configuration. I also was able to use full compiz functionality and it was fine. 

Of course you can go a step further by using lubuntu 10.04 too. Those are just my suggestions.

---

### Post by Linuxisfast on 2011-09-13
Strange, Natty x64 consumes max of 800 with Opera running whole day, this on a 1GHz AMD Fusion powered netbook with 2GB RAM.

In your case I would however suggest Lubuntu, all the stability and development of Ubuntu in a lighter package.

---

### Post by kimda on 2011-09-14
Always install a swap partition. If your machine runs out of physical ram it will then use the swap as an alternative. If you do not have a swap partition it will crash if you run out of ram. 

Unless its using swap all the time and your cache is almost 0 I would worry. Its normal behaviour for Linux to cache everything. You can also try xubuntu it also uses less memory. I've got a similar machine but with 2 gb mem and it only uses about 400mb even with Firefox and two tabs active on Natty. I would suggest to get 1 gb extra or a 2gb ram if you can.

---

### Post by whatthefunk on 2011-09-14
It would help to know what you use your computer for.  You said that Lubuntu is way to light...the only thing that has to be light about it is the desktop environment(even that can be changed though...).  Everything else can be purged and replaced.  The apps that come with lubuntu are light, but they can be replaced with better ones.

---

### Post by dan0804smith on 2011-09-14
> **whatthefunk said:**
> It would help to know what you use your computer for.  You said that Lubuntu is way to light...the only thing that has to be light about it is the desktop environment(even that can be changed though...).  Everything else can be purged and replaced.  The apps that come with lubuntu are light, but they can be replaced with better ones.

tell me more about this

---

### Post by whatthefunk on 2011-09-14
You can very easily delete the programs that come with Lubuntu and install ones that are more top your liking.  Say that you dont like Abiword, the default word processor program in Lubuntu, and want to replace it with LibreOffice.  First, delete Abiword.  You can either do this through the package manager (Menu > System Tools > Synaptic Package Manager) or by typing this in a terminal:
```
sudo apt-get purge abiword
```

Then, download and install LibreOffice using either the package manager or the terminal.
[```
sudo apt-get install libreoffice
```

You could do the same with mtPaint, the horrendous default graphics program in Lubuntu.  You could replace it with Gimp or Inkscape or whatever else you want.
Remove mtPaint with the package manager or in the terminal:
```
sudo apt-get purge mtpaint
```

Install Gimp through the package manager or in a terminal:
```
sudo apt-get install gimp
```

Everything in your Menu can be deleted and/or replaced so that you can truly customize your system.  This sounds like it would be ideal for you...it would allow you to have a light desktop environment that doesnt consume resources and also have all the programs you want.

---

