---
title: "calc does not remember where to freeze row?"
date: 2012-01-25
forum: General Help
---

### Post by qwertyjjj on 2012-01-25
I click on a row in Calc and select freeze so I can scroll down and still have some cells vidible at the top.
However, when I save, close, and reopen it, it does not remember the freeze option.
Any ideas how to do this?

---

### Post by squenson on 2012-01-25
If you save your file in the standard .ods format, it should work. If you save in another format, it is possible that this format doesn't support this information.

---

### Post by qwertyjjj on 2012-01-25
> **squenson said:**
> If you save your file in the standard .ods format, it should work. If you save in another format, it is possible that this format doesn't support this information.

Nope, is saved in .ods.

On another note, how can I add the shortcut to the file onto the panel launcher at the top?

---

### Post by squenson on 2012-01-25
Your profile may be corrupted. I suggest that you [reset it]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426#p58403"). Also, attach a copy of your file here, remove the cell content before, of course!

---

### Post by qwertyjjj on 2012-01-26
> **squenson said:**
> Your profile may be corrupted. I suggest that you [reset it]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426#p58403"). Also, attach a copy of your file here, remove the cell content before, of course!

resetting the profile didn;t do anything.
I try to freeze row 27 but it never remembers (attached).

---

### Post by squenson on 2012-01-26
Under Ubuntu 11.10 and LibreOffice 3.4.4., it works perfectly well. I could open your file and the first 26 rows were fixed and the scrolling started at the row 27. A save and open also worked.

Which version of Ubuntu and which version of OOo or LibreOffice do you use? Do you have the possibility to test it on another machine?

---

### Post by qwertyjjj on 2012-01-26
> **squenson said:**
> Under Ubuntu 11.10 and LibreOffice 3.4.4., it works perfectly well. I could open your file and the first 26 rows were fixed and the scrolling started at the row 27. A save and open also worked.

Which version of Ubuntu and which version of OOo or LibreOffice do you use? Do you have the possibility to test it on another machine?

ooo 3.2.1 and Maverick Meerkat

---

### Post by Hagar Delest on 2012-01-26
Works fine with OOo 3.3.0 on Ubuntu 11.10 too.
You can try to install the vanilla version. NB: LibO and OOo can run in parallel if installed with the websites .deb packages. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

