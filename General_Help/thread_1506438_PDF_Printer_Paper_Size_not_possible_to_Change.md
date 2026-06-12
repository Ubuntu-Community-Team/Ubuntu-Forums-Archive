---
title: "PDF Printer Paper Size not possible to Change"
date: 2010-06-10
forum: General Help
---

### Post by reef2dive on 2010-06-10
I have this issue with the paper size on PDF printer.
It is a standard installation, so no tweaks.

I cannot change the paper size of the printer. The setup is A4, but still when printing, the size will be locked to LETTER.

Please see attached pictures of Printer Settings and PDF printer paper size settings.

If anyone can point me to which file to change, or does it have something to do with privileges? Is there a specific group that the user has to be in to be able to access the settings?

---

### Post by gmargo on 2010-06-10
What application are you printing to PDF from?

What is in /etc/papersize?

---

### Post by reef2dive on 2010-06-12
/etc/papersize = a4
it was initially set to LETTER and was changed.

I am printing from thunderbird.

And I realized that thunderbird has the setting LETTER in Page Setup, which is not possible to override once when the print menu is open.

Thank you

---

