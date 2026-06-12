---
title: "Plymouth manager no splash screen"
date: 2012-04-20
forum: General Help
---

### Post by CardinalDirection on 2012-04-20
I recently used Plymouth Manager to change the loading screen displayed after Ubuntu is selected on the GRUB screen.  It was originally the default: the word Ubuntu with some dots changing colors.  I switched it over to something else, which worked.  I then changed it again.

It now just displays a black screen with a blinking cursor in the upper left corner instead of having an animated load screen.  It still displays the animation when my computer is shutting down, just not when it is starting.  Using Plymouth Manager to change it back to the default does not repair this.

I am using Ubuntu 11.10

Thanks

---

### Post by grahammechanical on 2012-04-20
I cannot give you much help but if you go to

file system /lib/plymouth/themes/default.plymouth

You can open the file default.plymouth in a text editor and see if it has

> ScriptFile=/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script

Plymouth Manager might have changed this and not changed it back. Clearly the Plymouth splash screen is not loading.

Regards.

---

### Post by CardinalDirection on 2012-04-20
> **grahammechanical said:**
> I cannot give you much help but if you go to

file system /lib/plymouth/themes/default.plymouth

You can open the file default.plymouth in a text editor and see if it has



Plymouth Manager might have changed this and not changed it back. Clearly the Plymouth splash screen is not loading.

Regards.

It does not have that line.  Should I add it and if I should, where should it go?

---

### Post by grahammechanical on 2012-04-20
This is the complete contents of my 11.10 default.plymouth

> [Plymouth Theme]
Name=Ubuntu Logo
Description=A theme that features a blank background with a logo.
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/ubuntu-logo
ScriptFile=/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script

That is all that is in the file. And it is the same for 12.04 which I am also using.

What changes did Plymouth Manager make? Did it change the file to point to another script?

Regards.

---

### Post by CardinalDirection on 2012-04-20
Oops.  I was looking at the wrong file.  It has exactly the same text as yours.

---

### Post by CardinalDirection on 2012-04-26
While this isn't really a solution, but the problem eventually resolved itself.  It went back to normal after I had the problem for a few weeks.  So to any of you future Ubuntu users who get this problem and can't find advice anywhere, don't loose hope.  Maybe it'll go away after a while.

---

