---
title: "Edit Grub"
date: 2012-03-18
forum: General Help
---

### Post by Miykel on 2012-03-18
G'Day; I just removed Ubuntu 11.10 by deleteing the partition but the entry is still in the grub bot loader, is there someway i can remove the 11.10 entry
Regards Miykel

---

### Post by plucky on 2012-03-18
> **Miykel said:**
> G'Day; I just removed Ubuntu 11.10 by deleteing the partition but the entry is still in the grub bot loader, is there someway i can remove the 11.10 entry
Regards Miykel

Does **sudo update-grub** remove it?

---

### Post by WasMeHere on 2012-03-18
Hi Miykel,

What other operating systems are there in your computer? If there is another linux system, it would be rather straight-forward with a linux tool from that system.
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

If you have only Windows or Mac-OS, I think you should use tools from that system.

Have fun finding out :-)
Olle

---

### Post by Miykel on 2012-03-18
G'Day and thanks so much, booted into 12.04 and run sudo update-grub,  done, all better.
  So simple when you know how, it's the know how thats difficult  lol.
Kind Regards Miykel

---

### Post by plucky on 2012-03-18
> **Miykel said:**
> G'Day and thanks so much, booted into 12.04 and run sudo update-grub,  done, all better.
  So simple when you know how, it's the know how thats difficult  lol.
Kind Regards Miykel

Can you mark this thread as solved using [color=red][Thread Tools][/color] at the top of the page.

Good luck

---

### Post by Bucky Ball on 2012-03-18
> **Miykel said:**
> 
  So simple when you know how, it's the know how thats difficult  lol.


Dunno, you seem to be doing alright ... ;)

There's also a neat little app called [Grub Customizer]("http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.htmlGrubCustomizer") you might like to have a look at/play with. Not sure if working in 12.04 LTS yet, though, but does some neat stuff. 

Could you please mark thread as Solved from 'Thread Tools'.

---

