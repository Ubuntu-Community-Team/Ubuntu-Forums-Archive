---
title: "how can i disassociate program from cd-rom drive?"
date: 2009-09-25
forum: General Help
---

### Post by the_guv on 2009-09-25
hey folks,

i installed the splendid cd-to-mp3 encoder "abcde" a few days ago.  when i inserted a cd, as you'd expect, up popped the dialogue asking with which programme to launch the music cd.

.. i chose abcde, and checkmarked to always use that. 

everything was great, until i decided i wanted to use the cd-rom drive with a different program association.

.. for the love of mike, i cannot work out how to change this program association and, for once (and it says a lot that this is a first) i cannot find the answer to my ubuntu problem in this ridiculously useful forum.  i even uninstalled abcde, but still the cd-rom drive is locked up, as really i'd have expected anyway.

i know it's a tiny edit in a .conf file - or i suppose so .. can anyone tell me which file to edit, please.  else, er, maybe a sledgehammer ..

many thanks,

olly.

---

### Post by scragar on 2009-09-25
```
gedit ~/.local/share/applications/mimeapps.list
```See if it's listed in there(I have no idea if it will or not, but it might be).

EDIT: I do know however it can be edited from inside nautilus(the default file manager), open the preferences, choose the media tab, then change your options under CD :p

---

### Post by StuartN on 2009-09-25
Open Nautilus file browser and Edit preferences. The CD/DVD actions are in the Media tab.

---

### Post by the_guv on 2009-09-27
@Scragar & @StuartN .. big cheers guys .. easy when you know how, huh. 

many tx.

---

### Post by StuartN on 2009-09-27
I bookmarked a link [http://thomas.apestaart.org/morituri/trac/wiki](http://thomas.apestaart.org/morituri/trac/wiki) about Morituri yesterday. It is a new (alpha) package that enables the use of AccurateRip in Linux - like Exact Audio Copy - so for audiophile accuracy (and occasionally reeaally slow rips) you might want to give it a try.

---

