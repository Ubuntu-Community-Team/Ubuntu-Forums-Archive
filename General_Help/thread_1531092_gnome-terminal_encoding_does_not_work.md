---
title: "gnome-terminal encoding does not work"
date: 2010-07-14
forum: General Help
---

### Post by Pustik on 2010-07-14
It seems to me that the Encoding (in Terminal -> Set Character Encoding) does not work. I am trying to get the Czech version of GNU gtypist to work, but it does not display properly.

In previous version of Ubuntu (Hardy), I could just switch to ISO-8559-2 and it displayed correctly. If I do this in current version (Lucid), the text remains messed up.

Characters input from keyboard display properly, regardless of the selected encoding.

I tried doing dpkg-reconfigure locales stuff as described on this forums, to no avail. Gtypist uses a very simple file (in ISO-8559-2 encoding), if I convert it to UTF-8 the program stops working (obviously it cannot read multibyte characters).

Please advise and thank you for your help.

---

