---
title: "Running my Windows partituin from Ubuntu"
date: 2006-04-07
forum: General Help
---

### Post by Hoffmann on 2006-04-07
Hi,

I have a Ubuntu-Windows xp dual boot system. Of course, I do prefer stay on  my Ubuntu partition. However, sometimes, I need to use some windows program. Well, I would like to run those programs from Ubuntu. What I want is some approach better than simply using Wine. As wee know, Wine is very limited; it is not possible to run several windows program with Wine.
So, could anyone, please, let me know how would be possible I run programs LOCATED into my windows partition, from Ubuntu?
I have no previous experience with that, and free programs/approaches would be preferable.

Thanks,
Hoffmann

---

### Post by aysiu on 2006-04-07
VMWare?
Crossover Office?
Another computer and a KVM switch?

---

### Post by T*&amp;1p87)v# on 2006-04-07
hmm, the only way I am now thinking of is usnig vmplayer,
but this means that you are not going to use your actual XP installation on the other partition, but simply start an XP installation as a virtual machine under ubuntu

btw what kind of porgrams do you want to run under ubuntu from windows.
I personally can watch movies for example by using ubuntu to run vmplayer with winXP and bsplayer, not that I am doing that regularly, I just tried it once and it worked :)

---

### Post by Hoffmann on 2006-04-07
[QUOTE=ayarov]hmm, the only way I am now thinking of is usnig vmplayer,
but this means that you are not going to use your actual XP installation on the other partition, but simply start an XP installation as a virtual machine under ubuntu

btw what kind of porgrams do you want to run under ubuntu from windows.
I personally can watch movies for example by using ubuntu to run vmplayer with winXP and bsplayer, not that I am doing that regularly, I just tried it once and it worked :)[/QUOTE]

I intend, for instance, to use Exceed. This is a X emulator, that permits to access UNIX machines (SGI, Solaris, etc) from windows. I mean, this way, you can see/use all of the graphic interface of those UNIX workstations under your windows OS. This is very useful, since one can access those mahines located in the lab (work)  from home. BTW, is there a powerfull emulator like that available for  Ubuntu linux?
Hoffmann

---

### Post by T*&amp;1p87)v# on 2006-04-07
Sorry no idea here, I have zero experience in running linux under m$win
good luck with your quest :)

---

### Post by aysiu on 2006-04-07
Maybe I'm not understanding how Exceed works, but I don't think Ubuntu needs to emulate X... it *uses* X.

Maybe you need something like VNC...?

---

### Post by Hoffmann on 2006-04-07
[QUOTE=aysiu]Maybe I'm not understanding how Exceed works, but I don't think Ubuntu needs to emulate X... it *uses* X.

Maybe you need something like VNC...?[/QUOTE]

Sorry, if my questions sounds 'stupid', but what is VNC?

---

### Post by T*&amp;1p87)v# on 2006-04-07
its remote desktop application as far as I recall

---

### Post by aysiu on 2006-04-07
[QUOTE=Hoffmann]Sorry, if my questions sounds 'stupid', but what is VNC?[/QUOTE] I don't know what it stands for, but it basically lets you view and/or control another computer from your computer. The other computer's screen appears as window on your screen. If you set up the VNC server to allow control, then you can actually move the mouse and click and type things on the other computer.

Tight VNC is nice because it exists for Windows and *nix:
[http://www.tightvnc.com/](http://www.tightvnc.com/)

I think there's also something called FreeNX that you may want to look into:
[http://freenx.berlios.de/](http://freenx.berlios.de/)

---

### Post by Hoffmann on 2006-04-07
[QUOTE=ayarov]hmm, the only way I am now thinking of is usnig vmplayer,
but this means that you are not going to use your actual XP installation on the other partition, but simply start an XP installation as a virtual machine under ubuntu

btw what kind of porgrams do you want to run under ubuntu from windows.
I personally can watch movies for example by using ubuntu to run vmplayer with winXP and bsplayer, not that I am doing that regularly, I just tried it once and it worked :)[/QUOTE]


Some more questions:
(1) In case that be my only alternative. Is it possible/tough to install the Win xp as a virtual machine under ubuntu? My machine is a HP, and my Windows  is the Media Center. Moreover, duting the real installation, a windows system recovery partition is also installed. So, it is a very big installation. Is it reasonable to do that under a Unbutu virtual machine, or the best option would be just to boot to the windows partition, instead?
(2) Is the VMplayer available for free?
(3) Does it work properly for you?

Hoffmann

---

### Post by T*&amp;1p87)v# on 2006-04-07
Well what I have and use is VmWorkstation which is not free, bet there are alternatives suchs as VMplayer, which I am sure is free. I have a virtual WinXPpro machine on my laptop with 512RAM and it works fine, of course it would be even better if I had more RAM.
As I said before I can even watch movies, well for real 3D apps I cannot guarantee anything, what I remember is that the guys from VMware are experimenting with Directx emulation or something so this 3d stuff is still in its early stages.
But apart from that I must say that if you go fullscreen with the virtual machine it would be hard to guess you are running it from ubuntu :) at least that is the impression I got so far :)
As for the case with M$ Media center I would say - try it out, read about it in the VMware page, I dunno if they support their emulation. Hope this info helps

---

### Post by s3a on 2007-07-28
Here ([http://ubuntulondon.wordpress.com/](http://ubuntulondon.wordpress.com/)) is a guide to emulating Windows XP under Ubuntu! It won't emulate you current partition but that's okay because all you need to do is copy the files to some external hard drive or something and then transfer them in Windows XP emulation under Ubuntu! I don't know much about this as I'm new to Linux but I going to try to attempt this because I have dial-up internet and it only works in Windows for now and until I can get it to work in Linux, I'll be using Windows emulation.

Anyway, I hope that helps!

---

