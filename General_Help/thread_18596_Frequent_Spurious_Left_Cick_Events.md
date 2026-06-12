---
title: "Frequent Spurious Left Cick Events"
date: 2005-03-07
forum: General Help
---

### Post by MYOB on 2005-03-07
Since upgrading to Hoary, I'm getting very frequent spurious left mouse clicks on my Vaio (nonamer touchpad attached as a normal PS/2 and configred as such, Intel i830GM graphics). I also upgraded to kernel 2.6.11 at the same time, if that has any chance of causing such problems. 

Somethings changed along the input path as my jogdial now works as a scrollwheel, but the system is almost unusable

The spurious clicks get more frequent with fast mouse movement, so it seems like it might be connected to that. There are none when the cursor is sitting still.

---

### Post by alastair on 2005-03-07
2.6.11 might have had some changes to touchpad operation - some folks might find it worse.

Try booting with kernel arg :

psmouse.proto=exps

i.e. ESC at grub, "e" to edit kernel line, add above and "b" to boot.

If this doesn't work, perhaps try kernel 2.6.10.

---

### Post by MYOB on 2005-03-07
that safe to not just 'try'?

I'm not using grub, so I'd have to shove that arg into lilo.conf

I do have a backup kernel installed if I manage to bugger it up, but with the 2 minute BIOS data check on this laptop (Why I'll never know) reboots take nearly 5 minutes apeice...

---

### Post by alastair on 2005-03-07
Well, just make a copy of the relevant kernel section in the lilo config file - modify the copy (give it a "test" title).

I think you should be OK. Worth a try.

---

### Post by MYOB on 2005-03-07
never mind, theres LOTS of mentions on the lkml that 2.6.11 minced ALPS touchpad support with... spurious left clicks. Seems I must have a pad thats being incorrectly detected as ALPS, which others are having

2.6.10 it is then/

---

