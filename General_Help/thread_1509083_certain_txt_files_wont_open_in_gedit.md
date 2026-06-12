---
title: "certain txt files wont open in gedit"
date: 2010-06-13
forum: General Help
---

### Post by ozzyxisxisxis on 2010-06-13
I have a few .txt files that when opened in gedit give me an error "Could not open the file - gedit has not been able to detect the character encoding"

HOWEVER, I can see some of the contents of the files (a few words) in the icon preview in nautilus. Also, I can open these documents in notepad (using wine) though I'd prefer to use gedit.

These might not all be txt files. I know one is directory of important phone numbers that was in some obscure format that could only be opened on a nokia phone. Like I said, my workaround is notepad but I'd greatly appreciate any suggestions on how to open without wine

thanks!

---

### Post by Ryan Dwyer on 2010-06-13
It's giving you that error because it contains one or more characters that are outside the usual ASCII range.

In gEdit, go to File > Open. Choose UTF-8 as the character encoding then open your file.

---

