---
title: "Libnotify: Annoying, Distracting, Unconfigurable"
date: 2009-10-22
forum: General Help
---

### Post by sammcj on 2009-10-22
Just did a fresh install of Xubuntu 9.10 (I previously had a borked 9.04 -> 9.10 alpha installed)
[B]
Does anyone else find _libnotify_ really, REALLY annoying?

-Is there any way to turn the thing off?
-Is there any way to configure the program?[/B]


The software seems as if it was somewhat rushed, judging by its often buggy behavior. (and yes I realise 9.10 isn't offical out yet...)

---

### Post by tubasoldier on 2009-10-22
> **sammcj said:**
> 
[B]-Is there any way to turn the thing off?
-Is there any way to configure the program?[/B]

sudo apt-get remove libnotify

That will turn it off.

---

### Post by sammcj on 2009-10-22
> **tubasoldier said:**
> sudo apt-get remove libnotify

That will turn it off.

A LOT depends on it now, including Thunar and most of the XFCE desktop.

---

### Post by ajgreeny on 2009-10-22
It would be a bit of a crunchy way to do it but try renaming the **libnotify.so.x** file in /usr/lib.  I have no idea how or even if it would work, but it seems worth trying.  If everything goes totally wrong and you can't even boot, you can restore it back to its original name using a live CD, so nothing lost.

I am using jaunty still, so the files may be elsewhere, but you get the idea.

---

### Post by sammcj on 2009-10-22
> **ajgreeny said:**
> It would be a bit of a crunchy way to do it but try renaming the **libnotify.so.x** file in /usr/lib.  I have no idea how or even if it would work, but it seems worth trying.  If everything goes totally wrong and you can't even boot, you can restore it back to its original name using a live CD, so nothing lost.

I am using jaunty still, so the files may be elsewhere, but you get the idea.

Funny, I thought of this, but that is pretty dirty, I wonder why on earth has this been implemented with not configuration options?

I know of at least another two people that want to disable it / reconfigure it.

---

### Post by sammcj on 2009-10-29
No one have any ideas?
It's a bloody pain in the neck?

To reiterate:

-How do you configure it? (Set time-outs, colours, applications)
-How do you disable it without removing other pages?
-Why has this been implemented without any easy method of configuration?


I'd write one myself, but I'm a network tech not a programmer.

---

### Post by bevant on 2009-10-29
I have an issue libnotify. It always appears as a black box with coloured lines through it. I have an ati card on my thinkpad r40.

---

### Post by cariboo on 2009-10-29
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1277268&highlight=libnotify"), it is in the closed Karmic section, but it may explain what is happening.

---

