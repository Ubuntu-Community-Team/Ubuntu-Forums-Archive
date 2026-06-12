---
title: "remove bling from grub"
date: 2011-12-07
forum: General Help
---

### Post by gcbzzzz on 2011-12-07
i'm now feeling like an idiot. is used to be so easy to edit /boot/grub/menu

the grub.d system is a mindf...mess. mindmess.

How can I:
1 - remove all and every kind of splash and shenanigans? (i want text until X is up)

2 - remove all 'quiet' from every grub option

3- be able to add kernel options "easily". e.g. edit /etc/grub.d/00_defaults and add them to one line

sorry for the grumpy tone. i blame my laptops switchable graphic card.

---

### Post by phidia on 2011-12-08
I have not used it but there is a [grub customizer]("http://www.omgubuntu.co.uk/2011/05/grub-customizer/") available that claims to alter several of grub's settings. You need to add to your software sources and then install-instructions, info, and more links are at the link I inserted.

---

### Post by gcbzzzz on 2011-12-08
thanks, but i think i found HALF of what i was missing.

i don't have to look into /etc/grub.d

what i want is in /etc/default/grub

there i can solve issue 2 and 3.

but the main issue #1 is still driving me nuts.

even setting grub to use console mode, and adding "nosplash text" options i still get the abominable, now in ascii, splash crap :(

---

### Post by gcbzzzz on 2011-12-08
finished reading about the grub customizer... it's mostly do add bling :(

---

