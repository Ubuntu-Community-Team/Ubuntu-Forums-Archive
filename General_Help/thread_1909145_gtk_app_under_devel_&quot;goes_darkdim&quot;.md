---
title: "gtk app under devel &quot;goes dark|dim&quot;"
date: 2012-01-14
forum: General Help
---

### Post by kline on 2012-01-14
i'm writing a gtk application in C and run into problem seconds after i launch the app:: it goes dim.  the "close button in  the upper corner is the only thing that works.  

i mis-remember there being a Programming section, so am posting here.  

occasionally, my firefox brower dims for several seconds; usually it clears after some moments.  the nutshedll is: during my development of this GUI app, what do i do to end the dimming of my app
?

tia.

---

### Post by TeoBigusGeekus on 2012-01-14
Any error messages you get when you launch it from terminal?
Could we see the source code?

---

### Post by kline on 2012-01-14
> **TeoBigusGeekus said:**
> Any error messages you get when you launch it from terminal?
Could we see the source code?

no error messages.  sure you can see what i've cobbled together.  if you send your email offlist, i'll wing back  a tarball.   FWIW: I'm new to gtk; from 1996--2002 or so i did 10-12k lines of C using the athena toolkit ... but that never went anywhere. gtk seems harder.  i am certainly  rusty

---

### Post by TeoBigusGeekus on 2012-01-15
Go to my profile and directly underneath my username you will see the Send Message button: choose send message via email.

---

### Post by kline on 2012-01-15
i'm not sure i believe this, but i may have fixed the problem: after several trillion years of trying.  i'll send the code once i re-check what i tried briefly only a few hours ago. i think it was 02:57 localtime when i said: "Bleep" and quit.  

meanwhile, other gtk questions remain, such as how i can invoke a popup with YES_OR_NO without g_signal_connect().  in other words, gtk isn't my father's Athena :-)

---

### Post by TeoBigusGeekus on 2012-01-15
> **kline said:**
> meanwhile, other gtk questions remain, such as how i can invoke a popup with YES_OR_NO without g_signal_connect().  in other words, gtk isn't my father's Athena :-)

If you want it to be a reaction to something else, I can't see how you could avoid a callback function.
Anyway, you can post some snippets of code and we could discuss them.

---

### Post by kline on 2012-01-16
> **kline said:**
> i'm not sure i believe this, but i may have fixed the problem: After several trillion years of trying.  I'll send the code once i re-check what i tried briefly only a few hours ago. I think it was 02:57 localtime when i said: "bleep" and quit.  

Meanwhile, other gtk questions remain, such as how i can invoke a popup with yes_or_no without g_signal_connect().  In other words, gtk isn't my father's athena :-)

wrong....

---

