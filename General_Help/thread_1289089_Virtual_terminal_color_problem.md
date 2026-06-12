---
title: "Virtual terminal color problem"
date: 2009-10-12
forum: General Help
---

### Post by Eric Christopherson on 2009-10-12
I'm running 9.04 and have noticed that the colors in the text-mode virtual terminals are messed up. I'm attaching screen shots for comparison. Basically, the bold/high intensity colors all show up as gray, and yellow shows up as a darker gray. Is there a fix for this? Should I report it as a bug? Is there a config file for the colors in virtual terminals?

I have an onboard ATI RS480 [Radeon Xpress 200G Series]. Colors look just fine in X.

---

### Post by collinp on 2009-10-12
I'm not really sure what would cause this; Are you sure it's not something with your monitor's color settings?

If there's absolutely nothing wrong that you can tell, it is more than likely a problem with your driver.

Your screenshot looks fine.

---

### Post by Eric Christopherson on 2009-10-21
It must be a driver problem. Colors display fine in X, and when I booted into my old Debian installation on the same computer and with the same monitor, the colors showed up correctly.

How do I find out what console driver I'm using, what version it is, how it's configured, etc.?

Also, I just noticed that sometimes when I boot, the splash screen disappears before X starts up. I can't figure out why it does that, because the text scrolls too quickly, and once it does launch X, if I go back to VT 8 I can't scroll up. Is there any way to find out why usplash is quitting?

---

### Post by OwnSurname on 2009-10-24
Not related to remote terminals, but I've the problem in the gnome terminal, under 9.04. I was setting up a coloured output using ls, and I noticed that if I set the option bold (01) for a type instead of none (00), the colors blue and cyan are switched. So if my file not bold was shown as blue, when bold is shown as cyan, and viceversa. There must be a mapping error somewhere, but I don't know how this work. Also, other colors are not affected.

EXAMPLE
.type 00;34 *type is shown blue, which is correct*
.type 01;34 *type is shown cyan, which is incorrect*

---

