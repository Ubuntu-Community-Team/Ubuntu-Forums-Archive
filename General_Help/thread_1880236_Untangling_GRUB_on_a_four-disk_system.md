---
title: "Untangling GRUB on a four-disk system"
date: 2011-11-13
forum: General Help
---

### Post by weyland42 on 2011-11-13
I'm trying to tidy up an Ubuntu 11.04 system which has four internal hard-drives, three of which have a version of Ubuntu installed (it's a long story).

It boots by default from **sdc**, and that's where the grub.cfg file is.

I want to use the 11.04 version on **sdd** and delete all the others. I know how to generate a current grub.cfg for **/boot/grub** on **sdd**, but I guess the BIOS will still pick up the one on **sdc**.

How can I get rid of the other Ubuntus safely and end up with a usable system?

[IMG]http://lh5.googleusercontent.com/-TLntZSwkpHE/Tr-278-Gp6I/AAAAAAAAIgQ/7gLJP6YgTLo/s800/P1040061s.jpeg[/IMG]

---

### Post by sanderd17 on 2011-11-13
First, try to switch the default boot order in your BIOS, and try to boot from sdd (it will be called different in your BIOS). That way, you will see what's in the bootloader of that disk (you will probably get another Grub screen). 

If you set your BIOS to boot from sdd, and you are able to boot Ubuntu on the same sdd, you can just reformat the other Ubuntu partitions (though I always think it's good to have one unused OS still installed. Just in case of.)

Oh yes, don't forget to note the current positions of your HDDs in you BIOS, in case you want to get back.

---

### Post by weyland42 on 2011-11-13
> **sanderd17 said:**
> First, try to switch the default boot order in your BIOS, and try to boot from sdd (it will be called different in your BIOS). That way, you will see what's in the bootloader of that disk (you will probably get another Grub screen). 

If you set your BIOS to boot from sdd, and you are able to boot Ubuntu on the same sdd, you can just reformat the other Ubuntu partitions (though I always think it's good to have one unused OS still installed. Just in case of.)

Oh yes, don't forget to note the current positions of your HDDs in you BIOS, in case you want to get back.

Heel veel bedankt, Sander. Problem solved.

---

