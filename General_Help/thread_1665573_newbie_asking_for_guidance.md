---
title: "newbie asking for guidance"
date: 2011-01-12
forum: General Help
---

### Post by budgetpro on 2011-01-12
Hello there, people who I have been told are the wizened "elders of the internet", I am simply a high schooler with an INTP personality, interest in computers, the internet and who has no idea where to begin :confused: . In middle school, I did very basic ground level HTML coding for simple web pages on the kids community Neopets, and have been strongly considering returning to have the motivation to get back into coding. Last year (freshman year) I watched some intro DVD's to Adobe Dreamweaver but hardly scratched the surface. I'm in basic Algebra simply because of my poor work ethic, I'd rather play around on the computer than do my work, but I like numbers and doing math and am very interested in the general mathematics/physics field.

I have my own computer at home running on Windows XP service pack 3 with basic hardware, given to me by an elderly woman who is a family friend, and whose son runs his own little IT support/repair/whatever out of his own home, and is practically my Obi-Wan. He hasn't taught me all that much, but caught my interest in computers and gave me the nudge I needed to actually begin researching rather than simply saying "I like computers" to people. 

One night I tried installing Ubuntu onto my PC, only to find I was unable to make my wireless card work with it. So I uninstalled it the same night after about a half an hour of lazy google searching trying to find a guide to making my wireless card compatible with Ubuntu. My only motivation for installing Ubuntu being the frequency I saw references to it,Linux (and all the various other “holy grails (from my understanding)” of the computer culture in various Internet comics, tv shows, etc., and wanting to feel nerdy with a different OS.

From the googling I’ve done, I’ve found that python would be the best coding language for me if i want to program software. I don’t really care what I program, at the moment, I just remember greatly enjoying it with my brief experience with Neopets and want to experience it again on a more complex scale.

Here’s the rundown of my computer, I’ll answer any questions that hopefully won’t intrude upon my privacy:


Intel
Celeron CPU 2.26 GHz
480 MB RAM

So my question is, mainly, Where/how do i start?

---

### Post by nothingspecial on 2011-01-12
Well the first thing you need to do is post your wireless card.

I`m not actually clear if you have ubuntu installed at the moment.

If not boot up a live cd.

Either way, open a terminal and post the output of 

```
sudo lshw -C network
```Which will show what Ubuntu is recognising your card as.

Before you do that, get a wired connection and in the menu go

system > administration > additional drivers and see if that finds anything for you.

With that much ram you may find Lubuntu easier to get started, and when you get going you can install your own customoized Ubuntu that will handle those specs.

---

### Post by Kirboosy on 2011-01-12
> **nothingspecial said:**
> With that much ram you may find Lubuntu easier to get started, and when you get going you can install your own customoized Ubuntu that will handle those specs.


Agreed. I would recommend Lubuntu for your pc. Ubuntu is pretty "heavy" compared to Lubuntu.

Unless you wanna put a little money and upgrade your RAM. 1 Gb would be the sweet spot for your computer.

---

### Post by budgetpro on 2011-01-13
> **nothingspecial said:**
> Well the first thing you need to do is post your wireless card.


Rosewill RNX-G300EX, and I can't do the rest because I took Ubuntu off my computer and am back on windows xp right now. Would I find Lubuntu on the same site? What's the difference?

---

### Post by Kirboosy on 2011-01-13
[lUbuntu]("http://lubuntu.net/") simply means Light Ubuntu, faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment.

It will look different than Gnome but I bet you will be happier with the speed increase.

Also, You don't need Ubuntu installed on your computer to do what nothingspecial instructed you to do. Just put the Ubuntu CD in the drive and boot off the CD. As soon as you reboot your computer will go back to normal.

---

### Post by budgetpro on 2011-01-13
I don't have the disk. i simply downloaded it off the website when I did it. I don't have money to spend on the shipping, as it a credit card or whathaveyou but i have money otherwise.

---

### Post by deserthowler on 2011-01-13
> **budgetpro said:**
> I don't have the disk. i simply downloaded it off the website when I did it. I don't have money to spend on the shipping, as it a credit card or whathaveyou but i have money otherwise.

You should be able to just download the iso and burn a copy of it to use as a live CD with no cost other than the CD involved.
Earl

---

### Post by Kirboosy on 2011-01-13
You can also use a thumbdrive (probably at least a 1 Gb) and make that bootable using [this]("http://www.linuxliveusb.com/")

---

### Post by migs73 on 2011-01-13
You don't need a credit card or cash, there is a scheme called 'ship it' which will send you it for free;

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

it could take upto 10 weeks though.

Was the original attempt to install a WUBI install (installed inside windows)?

It's not always the most reliable install (just for getting a feel for it) but a LiveCD will give you a better chance of it working.

If you could have a wired connection to the internet when doing it you can check and download any required drivers for your wireless card.

Let us know what you decide to do and we'll guide you through the processes you may need to do.

Regards

Mike

---

