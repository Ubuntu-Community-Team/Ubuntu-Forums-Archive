---
title: "please help... cant boot windows or ubuntu"
date: 2009-11-28
forum: General Help
---

### Post by r0tor on 2009-11-28
I had a Wubi install of 9.10 on Windows XP.

A few days ago after a ubuntu update, if i selected to boot in Ubuntu it would go directly to the sh:grub command prompt.  I was looking on the grub2 webpage and tried to follow some steps to reinstall grub from a live cd.

NOW I DONT HAVE AN OPTION OF BOOTING IN WINDOWS!!!  I start my computer and it just directly goes to the sh:grub command prompt.

How do I at least get my windows back?????

---

### Post by r0tor on 2009-11-28
bump

---

### Post by SuaSwe on 2009-11-28
Various stuff in here to try:

[http://ubuntuforums.org/showthread.php?t=1314064](http://ubuntuforums.org/showthread.php?t=1314064)

---

### Post by r0tor on 2009-11-28
i csnt load ubuntu from the prompt because then i get a kernel panic...

I just want windows back

---

### Post by SuaSwe on 2009-11-28
What have you tried so far, and what happened when you did?

---

### Post by r0tor on 2009-11-28
> **SuaSwe said:**
> What have you tried so far, and what happened when you did?

tried these steps... [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD


it apparently wiped out the grub so ubuntu was lost like before and now windows is gone as well

---

### Post by bluestar14 on 2009-11-28
try doing the recovery mode, then enter on the update option, if windows is still there it might find it

---

### Post by r0tor on 2009-11-28
so if i do...

root=(hd0,1)
chainloader +1
boot

I can get to windows... now how do i fix it?

---

### Post by r0tor on 2009-11-28
> **r0tor said:**
> so if i do...

root=(hd0,1)
chainloader +1
boot

I can get to windows... now how do i fix it?

Got to the windows recovery center and used FIXMBR... my computer boots windows again at least... yay

---

