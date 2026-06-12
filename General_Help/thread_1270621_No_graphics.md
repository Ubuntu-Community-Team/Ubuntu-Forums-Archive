---
title: "No graphics"
date: 2009-09-19
forum: General Help
---

### Post by Strange69 on 2009-09-19
I down loaded and installed an  ATI/AMD graphics program. I assume it installed drivers that are not compatible with my video card.  My problem is I cant boot up now to change them back to the old ones. 
Any help with this would be much appreciated. I can boot to the point where I get to choose which OS I want to use but then after selecting Ubuntu I get a screen full of color but no log in or anything else. I am kinda new to Ubuntu so pls forgive my ignorance. TIA

---

### Post by RedSingularity on 2009-09-19
Can you boot to a text console?  Should be a Recovery in the OS selection area that will give you an option to repair the xorg file.

---

### Post by Megrimn on 2009-09-19
**-k, what you need to do is:**

try booting the ubuntu recovery option in grub and then when it's done displaying text, highlight 'xfix' and hit enter, then when it's done, hit 'resume'

**-if that doesnt' work, then:**

when you are in grub, highlight the ubuntu os line and hit 'e' to edit the line.

then, highlight the 'kernel' line and hit 'e' again.

you should be in an editor for that line now.  what you need to do is add "xforcevesa" to the end of the line, without the quotation marks.

hit enter, and then hit 'b' to boot.  You should be able to get into it now to fix it.  Grub will not save what you added to the line, so you will not have to go back and fix it.

good luck!

---

