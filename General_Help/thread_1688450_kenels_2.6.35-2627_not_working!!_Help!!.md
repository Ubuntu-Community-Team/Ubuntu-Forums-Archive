---
title: "kenels 2.6.35-26/27 not working!! Help!!"
date: 2011-02-15
forum: General Help
---

### Post by iosuna86 on 2011-02-15
I am running Maverick and I have installed through the terminal those two kernel versions (26 and 27). 

Once I restart the system and choose either of those kernels to start, I can only work in console mode. 

I am using 2.6.35-23 without a problem and I have been having this same problem with version 25 too. 

Am I missing something? Can anyone help me out with this?

Thanks in advance!

---

### Post by davidmohammed on 2011-02-15
suggest when booting, display the grub by pressing and holding shift.

Choose one of the problem kernels - press e to edit.

Remove the text "quiet splash" 

press CTRL + X to boot.

Are there any error messages indicating what the problem could be?

---

### Post by iosuna86 on 2011-02-15
> **davidmohammed said:**
> suggest when booting, display the grub by pressing and holding shift.

Choose one of the problem kernels - press e to edit.

Remove the text "quiet splash" 

press CTRL + X to boot.

Are there any error messages indicating what the problem could be?

I have done what you suggested. There is no "quiet splash" text to remove when pressing "e". I am using Burg though, but a editable command prompt shows up after pressing "e", so I guess that's fine.

I see nobody is having trouble with this. 

I don't know what's wrong with my system.

---

