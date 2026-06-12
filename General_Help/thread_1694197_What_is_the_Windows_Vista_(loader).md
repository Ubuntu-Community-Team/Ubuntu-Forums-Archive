---
title: "What is the Windows Vista (loader)?"
date: 2011-02-24
forum: General Help
---

### Post by cblnchat on 2011-02-24
What is the Windows Vista (loader) when you start your computer and have to choose the ubuntu or the other operating system your running.  There are some other chioces too like ubuntu safe mode.  But whats the loader?  Ive never tried to use it since i have no idea what it does.
Thanks for the help

---

### Post by Mark Phelps on 2011-02-24
I'm guessing you're asking because you see this as a choice in the GRUB menu, right?

Selecting that will launch Vista, or, if you have Windows 7 installed, Windows 7.

The SW that creates the GRUB menu sometimes can't tell the difference between Vista and Win7 -- so it names it the Vista boot loader by default.

---

### Post by cblnchat on 2011-02-24
> **Mark Phelps said:**
> I'm guessing you're asking because you see this as a choice in the GRUB menu, right?

Selecting that will launch Vista, or, if you have Windows 7 installed, Windows 7.

The SW that creates the GRUB menu sometimes can't tell the difference between Vista and Win7 -- so it names it the Vista boot loader by default.

But i have Windows XP installed.  And i see that as a option too, but theres also an option for "Windows Vista (loader)" and im not sure what it does.
Does in install Vista too?

---

### Post by Dragonite on 2011-02-24
If you do not have Windows Vista installed, the "Windows Vista (loader)" will not work. GRUB cannot detect what version of Windows you are using, so it just lists them all. If you want to remove this option, see [here]("https://help.ubuntu.com/community/Grub2").

---

### Post by Chronon on 2011-02-24
It's possible that it is a recovery partition.

---

### Post by WorMzy on 2011-02-24
No, it won't install Vista. It may be a recovery partition though.

Run [this script]("http://bootinfoscript.sourceforge.net/") and it should give us more of an idea about what it may be.

---

