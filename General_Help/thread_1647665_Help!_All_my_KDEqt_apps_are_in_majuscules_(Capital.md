---
title: "Help! All my KDE/qt apps are in majuscules (Capital letters)"
date: 2010-12-17
forum: General Help
---

### Post by ubuntu27 on 2010-12-17
For some unknown reason all or most of my qt based application's font is in Caps. They are very hard to read. 

I will attach a image of Firefox and Rekonq for contrast.
As you can see from the picture, Rekonq is displaying everything in majuscule, while Firefox is fine.

How can I fix it?


Thank you all.

*******
I am running Kubuntu 10.10 64-bit

---

### Post by ubuntu27 on 2010-12-18
BUMPy doola

Please, I need your  help.

---

### Post by ubuntu27 on 2010-12-19
My last bump.


Thank you for your help in advance ^_^

---

### Post by Zorael on 2010-12-21
Do you have a **~/.fonts.conf** file? Try renaming it to something else and then restarting Rekonq. If that doesn't do it, try renaming **~/.kde/share/config/kdeglobals**.

---

### Post by ubuntu27 on 2010-12-22
Hi Zorael. Thank you for your help.

Your solution did not work.

I just found something interesting. If I check "Allow pages to choose their own font, instead of my selection above" in Firefox's preference, every letter becomes capitalized.

Hmm.. It affects every application that connects to the Internet such as Amarok's Lyric plugin.

I don't see any option on how to disable website selection of fonts in all the kde applications including rekonq.

---

