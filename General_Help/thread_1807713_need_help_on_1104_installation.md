---
title: "need help on 1104 installation"
date: 2011-07-19
forum: General Help
---

### Post by monte001 on 2011-07-19
please forgive if i post this on the wrong place.

i met a small problem while trying out ubuntu with all different versions that i can get hold of.

[http://ubuntuforums.org/showthread.php?t=1794580&highlight=monte001&page=2](http://ubuntuforums.org/showthread.php?t=1794580&highlight=monte001&page=2)

i am still struggling up to now.

if any one can help, i will be much appreciated.

monte

---

### Post by FormatSeize on 2011-07-19
If your computer is about 5 years old, then all signs point to a hardware issue. I would imagine that all of your hardware components, save perhaps the video and possibly the RAM, are the same age as the rest of the machine. There's really no real workaround for the problems that you are experiencing, as the seem to stem from hardware/software conflicts between your machine and Ubuntu 11.04. 
 
Generally, Ubuntu 11.04 will die laughing if you try to install it without a dual core processor and two GB of RAM. While your machine does have this, if it's an older computer, the technology still may not be such that is needed to properly run newer distros which, for whatever reason, want to eat as many hardware resources as possible. 
 
In my experience, I know that my machine will not run newer things like Fedora Core 15 with GNOME 3, and Ubuntu 11.04 with Unity. One day, bored out of my skull, I went and got a computer with a dual core processor, 4 Gigs of RAM, and so much HDD space that my apartment collapsed. It ran Gnome 3 with no problem (and I fell in love), and while Unity went fine, the Grub screen refused to recognize my monitor (it's about three years old), leaving me to guess at what I was going to boot into. 
 
I didn't keep the computer, as it was A Piece Of Crap That I Didn't Want, but it was a learning experience in that it let me know that I need certain minimal hardware requirements to run certain things. With this knowledge, I bought a used box from a consignment shop for about 150 dollars, took it apart and threw everything away except for the processor. I figured that all I needed was a dual core processor and I would be able to run Fedora 15 and Ubuntu 11.04. 
 
Boy, was I wrong. It wasn't only that they required dual core processing to run properly, but they wanted a dual core processor newer than a Pentium D, and RAM that wasn't DDR1. 
 
While it can be disheartening, there are, in fact, certain types of hardware that are largely incompatible with new Linux distros, or Linux in general.

---

### Post by monte001 on 2011-07-19
thanks formatseize for your detailed reply.

i am new to this area, and have the impression that linux is for most if not all old and new hardwares.

i keep trying testing, just hoping that i may be able to make use of an old machine for its economic life.

and at the same time, find something to do for my retired days.

once again, thank you very much for your help.

monte

---

### Post by Frogs Hair on 2011-07-19
If you want to look for other Linux distributions that may be more hardware friendly to your computer see the link . [http://distrowatch.com](http://distrowatch.com)

---

### Post by 3Miro on 2011-07-19
monte001: one of the advantages of Linux is the sheer numbe rof variations. Some of those work better on old hardware, some of them work better on new hardware.

Ubuntu 11.04 introduced the Unity interface, which is somewhat heavy on the resources. You can logout and select "Ubuntu Classic (No Effects)" for the classic interface, which is much lighter.

If you look for other distributions, you can take a look at the Desktop Environment. Gnome 2 is light, but they stopped supporting it and Gnome 3 is only a bit lighter than Unity. However, XFCE (check Xubuntu) is much lighter and faster, without really sacrificing on features. You also have LXDE (Lubuntu), but this one does sacrifice features for speed. There are also more extreme solutions like standalone OpenBox or IceWM, but those are probably best used by more experienced users.

---

### Post by monte001 on 2011-07-20
once again, i have to thank everyone for helping me.

i am facinated by the versatility of ubuntu.

i run it on my other machine, but it is this magic pro machine that gives me the joy of testing.

i tried a number of versions and cannot keep up with all your suggestions because i run out of hard disks. i keep some of the installed version for comparison.

up to now, it seems that the best result on this stupid machine is ubuntu 1104 with nomodeset and my self invented manuvre.

the 2nd best is LPS developed by us military defence. this version runs beautifully on the magic pro, but may be it cannot be installeld on the hard disk, or rather may be i don't know how to do it. each time, i have to boot from the cd.

i will keep testing, and may be share my experience if anyone feels that it may not be too trivial.

monte

---

### Post by grubbymitts on 2011-07-20
> **FormatSeize said:**
>  
Generally, Ubuntu 11.04 will die laughing if you try to install it without a dual core processor and two GB of RAM.
 
Seems to be working fine on my 7 year old Compaq Presario single core AMD with 1gb of ram.

---

### Post by monte001 on 2011-07-23
it should be marked solved as i tolerated the machine.

just quick update in case anyone is interested.

i continued to use my method to handle this machine and i could deploy ubuntu 1104.

but sometimes, the tapping of the key did not do the job, and i was left with a hanged screen.

the suggestion of looking into other version started me off to read more on the forum.

after many hours of trial and error, i came across puppy, which is a small volume version, but accepted my machine nicely, and worked very fast too.

and now i have been using ubuntu 1104 and puppy 525 on 2 different machines, i won't say happily ever after, but well contented.

thank you.

monte

---

