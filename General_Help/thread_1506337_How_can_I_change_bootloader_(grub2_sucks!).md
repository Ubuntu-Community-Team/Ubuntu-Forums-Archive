---
title: "How can I change bootloader (grub2 sucks!)"
date: 2010-06-10
forum: General Help
---

### Post by joaonunodias on 2010-06-10
Hi!

Why a fantastic SO like Ubuntu uses the worst bootloader I ever seen?

Grub2 sucks! My grub menu has 8 entries!!!! and I only have 2 SO (Windows Vista and Ubuntu).

I want to uninstall grub2 and use lilo or grub (I want the menu.lst back). How can I do that?

Thanks.


GRUB2 is TRASH!!:mad:

---

### Post by TheShader on 2010-06-10
Indeed man atm I'm having problems with it too! I just keep it for learning it. If I get p***** off like you I'll switch back too. You have to remove grub-pc and install grub from the package manager, then you have to configure grub. Take a look here:

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

---

### Post by A.M.Y on 2010-06-10
also there's the bug where grub2 fails when u boot with windows and restart.. some windows programs or recovery programs overwrite the grub2 and u gotta boot from a live CD and reinstall grub again.. bug #441941 @ launchpad.. really is there any other better bootloader ?  am sick of reinstalling grub every time i log 2 windows...

---

### Post by TheShader on 2010-06-10
> **A.M.Y said:**
> also there's the bug where grub2 fails when u boot with windows and restart.. some windows programs or recovery programs overwrite the grub2 and u gotta boot from a live CD and reinstall grub again.. bug #441941 @ launchpad.. really is there any other better bootloader ?  am sick of reinstalling grub every time i log 2 windows...

I guess it's the Windows's fault. The boot loader can't just resist to be overwritten! :) There should be some kind of configuration for Windows... But I don't know.

---

### Post by philinux on 2010-06-10
> **joaonunodias said:**
> Hi!

Why a fantastic SO like Ubuntu uses the worst bootloader I ever seen?

Grub2 sucks! My grub menu has 8 entries!!!! and I only have 2 SO (Windows Vista and Ubuntu).
I want to uninstall grub2 and use lilo or grub (I want the menu.lst back). How can I do that?
Thanks.
GRUB2 is TRASH!!:mad:

Just uninstall the old kernels from synaptic. It will auto run update-grub and you'll then have a trimmed down menu.

Or install startupmanager and choose how many kernels to display.

---

### Post by rahilm on 2010-06-10
OR try burg.. its based on grub2

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

---

### Post by joaonunodias on 2010-06-10
BURG seems nice!:p

I'm going to try. 

Thanks... very much:p

---

