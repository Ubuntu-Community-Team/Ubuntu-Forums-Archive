---
title: "Printing from DOSemu to cups-pdf"
date: 2010-03-12
forum: General Help
---

### Post by nead on 2010-03-12
Hi! My first post. Guess i have to point that out for some reason.
Anyway im trying to do a simple thing pointed out in the thread title.
Everything is set up, cups-pdf works, in dosemu.conf lpt1 command is "lpr" printer-timeout is 10...
I "work" in an accounting agency that has a program written in clipper back in 1992. :D
Apparently some prints from this program produce text/plain and some produce application/octet-stream.
text/plain is printed.
The later is always aborted. I have uncommented the lines in mime.types and 
mime.convs.
Which are located in /usr/share/cups/mime. 
What could/should i do? 
Thanks in advance.

---

### Post by nead on 2010-03-12
Ok. I solved this in a very straightforward way. In mime.types file on the line where it said application/octet-stream i just copied the rules for text/plain. Now it prints! It probably won't help anyone but here it is!

---

### Post by stefandebacker on 2011-08-01
> **nead said:**
> Ok. I solved this in a very straightforward way. In mime.types file on the line where it said application/octet-stream i just copied the rules for text/plain. Now it prints! It probably won't help anyone but here it is!

It helped me :P!! Thanks for this tip.

Greetings

---

