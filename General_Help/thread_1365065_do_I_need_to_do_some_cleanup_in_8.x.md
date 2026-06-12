---
title: "do I need to do some cleanup in 8.x ?"
date: 2009-12-26
forum: General Help
---

### Post by attilab on 2009-12-26
I understand that we don't have a registry in Ubuntu as in Windows but also assume there is something else what keeps a track about installed-uninstalled programs. Here is the storry:
- had some struggle with Vlc, did a fight with it's skin's and after some time just gave up. Several months later (today) I had again a need for its versatility so put it back and removed the Totem (with Add/Remove Applications). At least removed from the applications list, but again when I double-click the media file the Totem opens and plays it... That is a ?????? for me, want to learn these things a bit more what and how else to do things in future.
Is there anything out there we can use, to do some sort of cleanup? I was playing around a lot with bunch of staff in past months, many things got removed, but also I am sure there are the scars somewhere inside Ubuntu. Hesitating using KleanSweep before your input, pls advise the pros and cons.

---

### Post by oldos2er on 2009-12-26
To change the program a particular file type opens with, right-click on the file in question, click Properties, Open with.

Running **sudo apt-get autoremove** will uninstall any unneeded packages, such as dependencies that were installed with a given program that are no longer needed by the system.

Haven't heard of "Kleansweep".

---

### Post by warfacegod on 2009-12-26
If you prefer a GUI, then Ubuntu Tweak has some cleaning utilities. It also has many other useful features. Google will help you find it. I believe Computer Janitor comes installed in 8.x but be careful with that one. It tends to do bad things to my custom themes if I'm not careful.

---

