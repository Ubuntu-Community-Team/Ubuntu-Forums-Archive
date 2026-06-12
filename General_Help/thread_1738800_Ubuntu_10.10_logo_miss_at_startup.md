---
title: "Ubuntu 10.10 logo miss at startup"
date: 2011-04-25
forum: General Help
---

### Post by Jooon on 2011-04-25
Hi guys,
i've just upgraded ubuntu and i noticed that the ubuntu logo has been replaced with the text "Ubuntu 10.10".
When i boot ubuntu i get a black screen for 10-15 seconds and then the text and the five dots.
Before the desktop is loaded the computer shows some other text like those in verbose mode.

So, i know that this isn't a big problem, but there's a way to solve it?

Thanks,
Jon O:)

---

### Post by Frogs Hair on 2011-04-25
Hi and Welcome 

I am assuming the  upgrade was from  10.04 to 10.10  ?  Please give some system information and have you installed a proprietary driver for the graphics card ?

---

### Post by Spyderkid on 2011-04-25
Basicly (many people have this problem including me)

your graphics cards driver doesn't start up quickly enough to run the fancy graphics for ubuntu 10.10 because you've enabled a driver of a sort.

you've probably got a NVIDA card.

But yes its nothing to worry about at all

---

### Post by nankura on 2011-04-25
i had this same problem on every debian based linux when installing ATi drivers for my gfx card

It actually sounds like you havnt changed the boot manager

Go into the software center and get the package "Startup-manager" or something like that and itll be in your admin menu

itll bring up a little gui were you can edit your startup options, make sure  "show splash screen" is selected and that should fix the "text ubuntu 10.10" problem and show the visual logo

---

### Post by Jooon on 2011-04-25
Hi, and thanks for the quick answers!

@Frogs Hair
I'm sorry, i forgot the system info.
Upgrade 10.04 -> 10.10 [upgraded during first installation on HD]
nvidia drivers for GeForce 7600GT [v. 173.14.28]
one screen

something else:
-CPU: Intel Core 2 Quad @2.4GHz
-2GB RAM
-8GB Swap disk space
-76GB Ubuntu Partition
-3 HD [320GB, 320GB , 1.5TB - Seagate]

@Spyderkid
So a solution can be disable the nvidia drivers probably.
But i will lose the desktop effects doing so.

@nankura
Already checked startup manager before.


Yeah, so as usual is the graphic card the problem :(

---

