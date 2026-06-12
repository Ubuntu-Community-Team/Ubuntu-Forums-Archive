---
title: "Questions before installing ubuntu..."
date: 2010-07-18
forum: General Help
---

### Post by Nivyan on 2010-07-18
I've installed ubuntu several times in the past 3 years but ended up uninstalling it for different reasons (which seems to have been fixed now(!))

But I have a question before installing in which I hope someone can answer for me.

Is it possible to dualboot it with Windows 7 like this:
I start up the computer and everything boots completely normal into Windows 7.
BUT! If I hit the F8(i think it is?) and goto boot options- THERE I can choose to boot into ubuntu.

---

### Post by 23dornot23d on 2010-07-18
F8 from what I remember takes you into the windows recovery screen .....
boot normal or boot last good configuration etc .....

or are you

Meaning that it allows the choice of booting from another Disk

Using the BIOS settings ......

Do you have more than one disk drive ?

---

### Post by sisco311 on 2010-07-18
You can set Windows as the default OS and hide the grub menu:
[uhelp]community/Grub2[/uhelp]

---

### Post by Nivyan on 2010-07-18
> **sisco311 said:**
> You can set Windows as the default OS and hide the grub menu:
[uhelp]community/Grub2[/uhelp]

This pretty much.
  If I Hide the grub menu, how do I boot into ubuntu when I start my computer?

---

### Post by sisco311 on 2010-07-18
> **Nivyan said:**
> This pretty much.
  If I Hide the grub menu, how do I boot into ubuntu when I start my computer?

If you hold down the Shift key during the bootup, the menu will show up.

---

### Post by 1915flyer on 2010-07-18
Can't you just change the order of the selection in the grub menu so that the windows selection is at the top and is the default?

I don't know how to do it, but I remember seeing instructions in this forum.

PS: Did a search myself.
Find Startup Manager in the repositories. That will enable you to select the default OS

---

### Post by cchhrriiss121212 on 2010-07-18
> **1915flyer said:**
> Can't you just change the order of the selection in the grub menu so that the windows selection is at the top and is the default?

I don't know how to do it, but I remember seeing instructions in this forum.
Install startup manager, a nice and simple GUI for configuring GRUB.

---

