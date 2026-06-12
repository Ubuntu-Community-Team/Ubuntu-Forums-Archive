---
title: "Get Back into Ubuntu after Windows Install"
date: 2006-03-12
forum: General Help
---

### Post by Myrkul23 on 2006-03-12
I was running Windows and Ubuntu as a dual boot, and I just reinstalled Windows XP.  By doing that, I do not have access to the bootloader anymore and cannot enter into Ubuntu.

Is there a rescue command I can use on the Ubuntu install cd?  Also, once I get back into Ubuntu from the CD how do I re-initialize grub?  Thanks for any help.

---

### Post by Zelut on 2006-03-12
sure is.  Gotta love how Windows cleans off anyone else using the MBR..

You can find directions [here]("http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation")

---

### Post by Xian on 2006-03-12
[QUOTE=Myrkul23]Also, once I get back into Ubuntu from the CD how do I re-initialize grub?[/QUOTE]

# grub-install /dev/hdx

Where x=your partition letter.

---

