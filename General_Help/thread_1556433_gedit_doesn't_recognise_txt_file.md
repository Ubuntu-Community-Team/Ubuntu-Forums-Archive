---
title: "gedit doesn't recognise txt file"
date: 2010-08-19
forum: General Help
---

### Post by Man_Beach on 2010-08-19
I typed in a text file (Feb.txt) at work using the basic Microsoft Notepad text editor and emailed it home.
When I tried to open it from the email using the default gedit I got an error message - 

[INDENT]Could not open the file /tmp/Feb.txt
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.[/INDENT]

The character encoding is set to 'automatically detected'.

How come it can't detect the encoding? I had to manually set the encoding to Western(ISO 8599-15) to load it.
I can't remember this happening in the past, and it was OK loading one I sent earlier (Jan.txt) which presumably had the same encoding, as it was written in the same way.

---

### Post by Vaphell on 2010-08-19
run gconf-editor and check apps > gedit-2 > preferences > encodings.

autodetected key defines the order at which gedit attempts to recognize valid encoding

---

### Post by Man_Beach on 2010-08-20
Simple, when you know how!

---

### Post by sakishrist on 2011-09-04
+1 for the solution!

---

