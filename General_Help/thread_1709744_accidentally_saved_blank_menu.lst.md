---
title: "accidentally saved blank menu.lst"
date: 2011-03-18
forum: General Help
---

### Post by magnit2 on 2011-03-18
Hey guys I installed ubuntu 10.10 alongside WIN XP about 2 months ago, and today I decided to change the boot list order of grub. I did the "gksudo gedit /boot/grub/menu.lst" to access the menu.lst file, and it was blank. The problem is, I accidentally saved the blank menu.lst file in /boot/grub. now it appears next to the menu.lst.save, and i can't move it to trash. I haven't restarted out of fear of losing the ability to boot. 

Please help!

---

### Post by grahammechanical on 2011-03-18
Can you not edit it with the same command that let you blank the file in the first place. Copy the information from menu.lst.save into menu.lst. Or edit it and save it with a new file name and then edit menu.lst.save and save it with the file name of menu.lst.  

Or run sudo update grub.

I am not saying any of this will work but it might do.

Regards.

---

### Post by coffeecat on 2011-03-18
The reason you got a blank menu.lst is that there is no menu.lst in Ubuntu 10.10. So saving a blank menu.lst will not affect the functionality of grub.

The file menu.lst belongs to legacy grub which hasn't been used in Ubuntu since the now end-of-life Jaunty/9.04. Maverick/10.10 uses grub 2.

Grub 2 is more complex to configure. If you need to do this, have a look here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by magnit2 on 2011-03-18
Thanks so much guys, I did a restart just now and no problems. Just a little overreaction I guess :P

Thanks a bunch.

---

### Post by pqwoerituytrueiwoq on 2011-03-18
> **coffeecat said:**
> having a blank menu.lst will not affect the functionality of grub.
not if you revert it to legacy grub or updated from something before lucid lynx

---

### Post by coffeecat on 2011-03-19
> **magnit2 said:**
> Hey guys I installed ubuntu 10.10 alongside WIN XP [COLOR=Red]about 2 months ago[/COLOR]

> **pqwoerituytrueiwoq said:**
> not if you revert it to legacy grub [COLOR=Red][COLOR=Red]or updated from something before lucid lynx[/COLOR][/COLOR]

:wink:

**EDIT**: Oh, by the way, pqwoerituytrueiwoq, if you are going to quote another post, please do not change what was said. That is simply bad netiquette. You changed the wording of what I was saying to magnit2 as well as wrenching it out of context, thus changing its meaning.

---

