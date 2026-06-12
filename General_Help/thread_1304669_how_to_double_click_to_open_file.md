---
title: "how to double click to open file?"
date: 2009-10-29
forum: General Help
---

### Post by ProDigit on 2009-10-29
I have ebooks from my sony reader that I can read in a program called Calibre LRF Reader.
The program works nice, but if I right click the default action on an LRF file is 'execute'.

I have to right click, and then select 'open with' and select the reader program

How can I change it to the default action by double clicking?

I'm using Xubuntu updated to the latest updates...

thanks!

---

### Post by hwttdz on 2009-10-29
There are a few things that might be off, first you're going to want to change permissions to 644, or right click, properties, user -> read/write, group&other -> read (or just "chmod 644 filename" at the terminal).  Then you're going to want to right click and go to properties, and change the default open with option to your reader program.  Hope that helps.  Let me know if you have further troubles.

---

