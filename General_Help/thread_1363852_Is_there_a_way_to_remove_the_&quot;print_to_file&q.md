---
title: "Is there a way to remove the &quot;print to file&quot; option in the print dialog?"
date: 2009-12-25
forum: General Help
---

### Post by TwistedLincoln on 2009-12-25
Is it possible to remove the "print to file" option in the GNOME print dialog?  I have cups-pdf installed, and some of my users get confused as to which option to use.  

Since the "print to file" option doesn't auto-generate a filename (which causes the file to be hidden by default if you don't change it from .pdf), I'd like to remove the option entirely to avoid this confusion.

Is this possible?  I couldn't find any gconf key that was applicable.

---

### Post by TwistedLincoln on 2010-01-19
Can anyone offer a suggestion?

---

### Post by overboostsrt4 on 2010-05-28
I could use some help with this as well

---

### Post by TwistedLincoln on 2010-06-04
Really?  Only myself and one other person finds this annoying?

Surely there is a workaround out there somewhere.

---

### Post by blades171 on 2010-10-27
i am trying to find a way to do it too.
or just have it not be default when you log in to a tsclient.

---

### Post by sonson on 2012-11-22
Solved in ubuntu 11.04 with libgtk2.0-0
Just delete this file:
/usr/lib/gtk-2.0/2.10.0/printbackends/libprintbackend-file.so
And you will not see  print to file !!!

---

### Post by wildmanne39 on 2012-11-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

