---
title: "Is it possible to dual boot 8.10 and 9.10?"
date: 2009-11-14
forum: General Help
---

### Post by waynefoutz on 2009-11-14
My laptop has an ATI radeon x1270. After 3 days researching, trial and error, I learned that my graphics system would never live up to it's 3d gaming potential unless I install 8.10. The newer ATI drivers are not compatible with my graphics card, and 9.04 and 9.10 are incompatible with the old driver. So, I installed 8.10, and it works amazing. But now I'm thinking I'd also like to put 9.10 on my system, just so I can keep up with the leading edge. 9.10 looks great when I had it installed, I had compiz working, but I had no 3d. So I'm thinking I'd use 9.10 for everyday stuff, and when I want to play a game, I could just boot up intrepid. 

The question I have is concerning Grub. Will it automatically add the second OS? Is it a pretty straight forward operation like it is dual booting with windows, or is there something I should be aware of? It took me a few hours of tinkering to get this intrepid install working, I don't want to start over because I did something stupid.

---

### Post by RedSingularity on 2009-11-14
Yeah just install the wanted OS beside the currently installed one.  Grub will set itself up.

---

### Post by maybeway36 on 2009-11-14
What I would do: Make a new partiton for 9.10 and install it there. Tell it to use that partition and not to format the 8.10 partition. That way, the new GRUB should be the default boot loader, and it will automatically detect your 8.10 install.

---

### Post by williejones on 2009-11-14
I tried to load 9.04 with 9.10 yesterday.  The 9.10 was already on my machine.  Grub defaulted to 9.04, so I let it load.  It got into a loop such that I had to reload 9.10 to use
the whole disk to boot.

I would like to have 2,(one for 9.10 and one for Lucid development) but I can't figure out how as Lucid uses 9.10 to load?

---

### Post by dcstar on 2009-11-14
> **waynefoutz said:**
> 
........
The question I have is concerning Grub. Will it automatically add the second OS? Is it a pretty straight forward operation like it is dual booting with windows, or is there something I should be aware of? It took me a few hours of tinkering to get this intrepid install working, I don't want to start over because I did something stupid.

You will not be able to have a /home partition shared between the two different releases because the different versions of Gnome (and the Gnome apps) may not play well together.

Apart from that, you can multi boot as many releases as you like.

---

