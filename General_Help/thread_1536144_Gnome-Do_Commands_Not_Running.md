---
title: "Gnome-Do Commands Not Running"
date: 2010-07-21
forum: General Help
---

### Post by intali on 2010-07-21
Hey guys,

I've just installed gnome-do, and some of the features seem to be working great, others not so much.

So, for the working parts, mostly launching any programs is going fine (matlab, terminal, chrome, etc.,).

What I'm having a problem with is launching anything else. I've enabled some of the add ons (file launcher, google contacts, pidgin, rythmbox, etc.,), and the results for these queries come up (eg typing "my document.xls" brings up a result), but hitting enter on these results just ends up causing the gnome-do to dissapear without launching anything.

I installed gnome-do from the software center, and have tried the following code which I found on the forums:
sudo aptitude install gnome-do-plugins
Which didn't seem to resolve the issue.

Running 10.04 LTS

Any ideas on how to fix this? Thanks!

---

### Post by sungod84 on 2010-07-24
I ran into the same problem when I started using the search file command in Gnome-Do. One think I noticed is that when you type your file name and it shows up, be sure to check what command it is doing in the right window of the app. If it says "run", it will do exactly what you have experienced. Either tab to the right window and use the arrow keys to select "open", or you can use the mouse to select what you would like Gnome-do to do with the file as well.

---

### Post by intali on 2010-07-26
> **sungod84 said:**
> I ran into the same problem when I started using the search file command in Gnome-Do. One think I noticed is that when you type your file name and it shows up, be sure to check what command it is doing in the right window of the app. If it says "run", it will do exactly what you have experienced. Either tab to the right window and use the arrow keys to select "open", or you can use the mouse to select what you would like Gnome-do to do with the file as well.
Worked great -- can't believe that I had such a silly problem. Thanks!

---

