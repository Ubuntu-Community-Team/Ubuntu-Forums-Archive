---
title: "mousepad close delay"
date: 2011-07-28
forum: General Help
---

### Post by maclenin on 2011-07-28
Just a quick observation from within Natty (11.04)....

I have noticed that it takes **mousepad** nearly 11 seconds to close. This behavior occurs after making/saving a single change (lasting a few seconds), or after making several changes and working within the document over several hours - and once I click the "x" or select "Quit" from the File menu, to close the application. 

Similar **mousepad** post-working closure procedures in Intrepid (8.10), were always instantaneous.

Thanks for any thoughts.

---

### Post by Toz on 2011-07-28
I experience the same. Apparently its somehow related to the clipboard and copy/paste actions. Here are some bug report links:
- [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568759]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568759")
- [https://bugzilla.xfce.org/show_bug.cgi?id=7588]("https://bugzilla.xfce.org/show_bug.cgi?id=7588")
- [https://bugzilla.xfce.org/show_bug.cgi?id=6521]("https://bugzilla.xfce.org/show_bug.cgi?id=6521")

It's apparently fixed in xfce4-settings-4.8.2 (which I believe is only available in oneiric right now). Suggested workarounds/solutions include:

- deleting your mousepadrc file (so it gets recreated)
- purging or downgrading **xfce4-clipman** and **xfce4-clipman-plugin**
- replacing xfce4-clipman with another clipboard package like parcellite

Unfortunately, none of the solutions worked for me.

---

