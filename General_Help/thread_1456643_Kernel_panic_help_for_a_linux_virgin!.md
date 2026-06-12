---
title: "Kernel panic help for a linux virgin!"
date: 2010-04-17
forum: General Help
---

### Post by naurispunk on 2010-04-17
Hi!

So I have a Ubuntu 9.10 running along side with windows xp now. And when i start my pc in GRUB In case i choose the first Ubuntu linux version (2.6.31-20-generic) I get Kernel Panic error. Thankfully if choose the another Ubutntu (2.6.31-14-generic) everything works. 

But anyway, what should i do in this situation? Should i try and uninstal linux version (2.6.31-20-generic) that doesnt work?  Or just remove it from GRUB list?

What i am afraid is that next time I accept the updates (which i always do cuz i just assume they are needed :)  ) I will end up with two versions of not-working Ubuntu in my GRUB Boot list.

---

### Post by nitstorm on 2010-04-17
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

You can use that and uninstall the kernel that gives you the Kernel Panic error. Hope this helps. Cheers :D

---

### Post by shaquille on 2010-04-17
There is a known bug in wubi.
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10](http://sourceforge.net/apps/mediawik...lems:Wubi_9.10)
__________________
Let us know what works and to mark your thread as [SOLVED], use Thread Tools on forum page.

---

