---
title: "Python consumes extremly lot of ram usage..."
date: 2010-04-06
forum: General Help
---

### Post by vickoxy on 2010-04-06
Hi,
i noticed few times that my ram usage in gnome increases high. So i found that python is using more than 500 MB Ram. Normally i didn´t notice this python. What does it do?

I am not sure, but i think that these increasing has something to do with skype/empathy (i think it grows after using this programs...

So, i killed the process and ram usage is normal.

Any clue?

---

### Post by Mighty_Joe on 2010-04-06
Python is an interpreter. You need to isolate which application Python is running. 
There's a [bug reported against Empathy]("https://bugzilla.gnome.org/show_bug.cgi?id=599850") for excessive memory use. Whether that memory use is actually "excessive" or if there is a memory leak in Empathy is a question for the Gnome developers.  If you want to pursue this issue, your best bet would probably be to use the contact information on the [Empathy]("http://live.gnome.org/Empathy") home page.

---

### Post by vickoxy on 2010-04-06
> **Mighty_Joe said:**
> Python is an interpreter. You need to isolate which application Python is running. 
There's a [bug reported against Empathy]("https://bugzilla.gnome.org/show_bug.cgi?id=599850") for excessive memory use. Whether that memory use is actually "excessive" or if there is a memory leak in Empathy is a question for the Gnome developers.  If you want to pursue this issue, your best bet would probably be to use the contact information on the [Empathy]("http://live.gnome.org/Empathy") home page.

Probably you are right-i tried to do something with empaty and after that i had this issue...

Thanks

---

