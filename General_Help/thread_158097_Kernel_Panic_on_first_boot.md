---
title: "Kernel Panic on first boot"
date: 2006-04-10
forum: General Help
---

### Post by Matt342 on 2006-04-10
Hello Everyone!

I am new here.

I just installed Ubuntu Breezy and when I first boot I get a Kernel Panic.

Kernel Panic - not syncing: Fatal exception in interrupt.

How can I solve this problem?

Matt

---

### Post by Matt342 on 2006-04-10
My Specs are:

2.8ghz Celeron
1GB RAM
Nvidia GeForce FX 5200 (PCI)
Mouse, Keyboard, CD/DVD Drive, 2 Network Cards

Sorry for not posting earlier 

Matt

---

### Post by rjwood on 2006-04-10
[quote=Matt342]My Specs are:

2.8ghz Celeron
1GB RAM
Nvidia GeForce FX 5200 (PCI)
Mouse, Keyboard, CD/DVD Drive, 2 Network Cards

Sorry for not posting earlier 

Matt[/quote]
did you install from a burned iso?

---

### Post by Matt342 on 2006-04-10
I got the Breezy CD and I installed from it.


[QUOTE=rjwood]did you install from a burned iso?[/QUOTE]

---

### Post by Paulus on 2006-04-10
Would it be rash to suggest a complete re-install of ubuntu?  Kernel panic on first boot is most certainly rare, could well be corrupt cd or somewhat.

Was it a CD sent to you, or did you burn it yourself?

I assume your hardware is stable (at stock or known to be stable oc´d) ?

---

### Post by Matt342 on 2006-04-10
I burned the CD myself. I will redownload and reburn the CD.

Matt

---

### Post by rjwood on 2006-04-10
[quote=Matt342]I burned the CD myself. I will redownload and reburn the CD.

Matt[/quote] 
Burn it slowwwwwwwwwwwww 4x  as an iso

---

### Post by Matt342 on 2006-04-10
OK and Thanks

---

### Post by Matt342 on 2006-04-10
Still doesnt work :(

---

### Post by Matt342 on 2006-04-11
Someone HELP!!!!!!!!!!!!!!!!!!!!

---

### Post by yamagami on 2006-04-11
I had the same problem. Actually, i'm so used to boot twice now that i might still have it and i'm not aware. I boot into the GMD, and instead of loggin in i automatically reboot and log in on the second try. 

I did upgrade to a i686 kernel and i *THINK* that it could have solved it. Give it a go. I'd love to hear if you do find a solution to this. I"ll keep trying myself.

btw - there's another past-post about this. you're not the only one... ;o(

---

### Post by Matt342 on 2006-04-11
Thanks! I will try it. I appreciate your quick response.

Matt

---

### Post by Matt342 on 2006-04-11
When do I choose the kernel? What is GDM? How can I upgrade to a kernel if I cannot boot to the OS?

Matt



[QUOTE=yamagami]I had the same problem. Actually, i'm so used to boot twice now that i might still have it and i'm not aware. I boot into the GMD, and instead of loggin in i automatically reboot and log in on the second try. 

I did upgrade to a i686 kernel and i *THINK* that it could have solved it. Give it a go. I'd love to hear if you do find a solution to this. I"ll keep trying myself.

btw - there's another past-post about this. you're not the only one... ;o([/QUOTE]

---

### Post by yamagami on 2006-04-11
Ok, 
The GDM is the first graphical screen that loads up when you start ubuntu, the one that asks for your username/password etc.

What i do to avoid the crashes is simply boot a second time. Once I turn on the laptop and get to the GDM, i immediatly select to reboot the machine and go through the boot process again.  I assume (and hope) that this time your desktop would not crash.

To install a new kernel the easy way, open Synaptic in Gnome:
System menu -> Administration -> Synaptic Package Manager.
There do a search for the word kernel, and pick linux-image-2.6.12-10-686.
Mark it for installation and click apply. Make sure you pick the 686 one. 

If you cannot access gnome, from the terminal type:

sudo apt-get install linux-image-2.6.12-10-686

After installation, reboot the computer and choose that kernel (686) in the grub loader kernel list (the first menu that should appear once you start your computer - still in 'text' mode).

Let me know if that helps the situation or not. I've never consciously got round to see if it crashes or not, but I guess I would have noticed if it did. 
It will however give you a significant boost in performance and boot time (well - it did for me. My laptop flies now...). 

Good luck 
I'll wait for your 'report' ;o)

Harel

---

### Post by Ramses de Norre on 2006-04-11
Don't think he gets to gdm.. I have no idea what causes your error though.
Does a live cd work?

---

### Post by Matt342 on 2006-04-11
I dont get the GDM at all. I never tried a live cd.

Matt

[QUOTE=yamagami]Ok, 
The GDM is the first graphical screen that loads up when you start ubuntu, the one that asks for your username/password etc.

What i do to avoid the crashes is simply boot a second time. Once I turn on the laptop and get to the GDM, i immediatly select to reboot the machine and go through the boot process again.  I assume (and hope) that this time your desktop would not crash.

To install a new kernel the easy way, open Synaptic in Gnome:
System menu -> Administration -> Synaptic Package Manager.
There do a search for the word kernel, and pick linux-image-2.6.12-10-686.
Mark it for installation and click apply. Make sure you pick the 686 one. 

If you cannot access gnome, from the terminal type:

sudo apt-get install linux-image-2.6.12-10-686

After installation, reboot the computer and choose that kernel (686) in the grub loader kernel list (the first menu that should appear once you start your computer - still in 'text' mode).

Let me know if that helps the situation or not. I've never consciously got round to see if it crashes or not, but I guess I would have noticed if it did. 
It will however give you a significant boost in performance and boot time (well - it did for me. My laptop flies now...). 

Good luck 
I'll wait for your 'report' ;o)

Harel[/QUOTE]

---

### Post by yamagami on 2006-04-11
Then try this from terminal:

sudo apt-get install linux-image-2.6.12-10-686

---

### Post by Matt342 on 2006-04-11
How do I get into the terminal if I get a Kernel Panic Error and then everything hangs?

Matt


[QUOTE=yamagami]Then try this from terminal:

sudo apt-get install linux-image-2.6.12-10-686[/QUOTE]

---

### Post by edwina on 2006-04-11
A live CD is not a bad idea, to give you an idea of where your problem might lie. If the live CD works then it is probably an installer problem, in which case I suppose you might try a different distro or wait for Dapper Drake to come out in a few weeks.

Not much help, I'm afraid, but at least it gives you somewhere to start.

Good luck!

---

### Post by Matt342 on 2006-04-11
I tried Dapper Drake Beta and still no luck. :(

Matt

[QUOTE=edwina]A live CD is not a bad idea, to give you an idea of where your problem might lie. If the live CD works then it is probably an installer problem, in which case I suppose you might try a different distro or wait for Dapper Drake to come out in a few weeks.

Not much help, I'm afraid, but at least it gives you somewhere to start.

Good luck![/QUOTE]

---

### Post by yamagami on 2006-04-11
Matt, I'm sorry I must have misread. When you turn on the machine and get to the grub boot menu, do you have an option to load some sort of recovery mode?
A live CD might be a good option to rule out an installer problem, as noted above. 
Harel

---

