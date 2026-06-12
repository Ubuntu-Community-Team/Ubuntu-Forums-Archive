---
title: "Share SSD between 2 Computers?"
date: 2011-11-16
forum: General Help
---

### Post by kirdie on 2011-11-16
I have a Desktop PC with an SSD and I plan on buying a laptop. Buying another SSD is too expensive for me however and I got used to the speed of the SSD.

My idea is thus to share the SSD between the two computers, switching it in and out everytime I use one of them. My question is now, however, how to best do that.

At the moment I have a 10GB Linux Partition (I think EXT-something) and a 100 GB NTFS partition for windows and some windows programs/data on it.

It would be ideal for me if I could just use the same partition for both PCs so that I have the same programs and configuration and everything, but that could be problematic as both would require different drivers. Is it possible to put in "branches" that load certain stuff depending on the computer detected?

Or would it be better to just create 2 more partitions, 1 for the Laptop Ubuntu and one for shared data. Or move all shared data (my home folder) to the NTFS partition, shrink the desktop Ubuntu partition to like 5 mb and create a second partition just for the laptops Ubuntu. However then I have to do everything I do in the GUI and OS twice (for example I have a terminal as a background). Could there be done something with links? Is it then possible on boot to automate which computer uses which partition? I don't want to have to choose in a boot manager in each boot.

What would be the best course of action for me here?

---

### Post by jjex22 on 2011-11-16
My initial inkling is that windows is not going to let you do the first one - it won't even run from a USB device without a lot of help, I had to use esata to banish windows to the little black box.

In terms of ease then I'd definitely say having two partitions would be the easiest, of course the problem is that windows vista/7 are so damn space hungry that you probably don't want to carve up any more space than you have to.

Another option would be a live distro - the whole point of these is to boot up on almost any hardware - you do what is called a frugal instal - sort of copying the cd to the hdd, then when you run it on a new machine, it detects the hard ware and boots to ram. There are a lot of these around now more people have 512 ram and above (so you can use them for more than just the basics), and would be my personal choice!

I can't testify as to getting a distro like ubuntu to recognise 2 machines, because I don't know, but I can foresee a headache - I've had issues when a graphics card failed and ubuntu was set to use the card not the integrated graphics, but I'm sure others will know the answer!

Edit just to give you an idea of choice - i just did a search for live medium distros on distro watch which returned 193 results! most of these would not fit the purpose, but [Puppy]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") and [slax]("http://www.slax.org/") are distro's I've used with a lot of success. in the instance of puppy be sure to check out their 'spin offs' or puplets - some are quite interesting, I remember one designed for gaming that came packed with just about every emulator imaginable!

---

### Post by jjex22 on 2011-11-16
Oh and btw - just noticed, Welcome to the forums! ):P

---

