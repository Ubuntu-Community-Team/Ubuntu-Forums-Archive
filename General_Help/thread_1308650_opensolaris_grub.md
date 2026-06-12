---
title: "opensolaris grub"
date: 2009-10-31
forum: General Help
---

### Post by eatsubway on 2009-10-31
hello,

I'm sure this question has been asked many times before but I've had difficulty locating a solution.

I recently installed opensolaris, in an attempt to triple boot with ubuntu, solaris, and win7.  After the installation, I am still greeted with the ubuntu grub loader which only has ubuntu and win7 just has it had before the intallation. I would like to solaris to be in the grub, which would bring me next to the solaris grub (I've read that the ubuntu grub can't boot into solaris directly) OR begin with the solaris grub than enter windows or ubuntu from there.

I've added these entries to menu.1st but no of them loads the Solaris grub when clicked on.

title OpenSolaris1
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

title OpenSolaris2
rootnoverify (hd0,1)
makeactive
chainloader +1
boot

title OpenSolaris3
rootnoverify (hd0,2)
makeactive
chainloader +1
boot

I have two hard drives. windows7 and ubuntu on the first and a second with just solaris. Let me know if more specs are needed.

Thanks for any help.

---

