---
title: "reset/restore ubuntu layout ?"
date: 2011-06-21
forum: General Help
---

### Post by Gordonisnz on 2011-06-21
Hello. I've got Ubuntu 10.04 LTS.

I've heard from a friend that I can 'reset' my ubuntiu layout to the standard/default 

But I googled & found one answer - Tried it & both my main menu & panels dissapeared 

(they reappeared when I re-booted)...


Basically I want the standard/default layout  when an ubuntu C is first installed (but of course, keepng any programmes ive added)

---

### Post by sanderd17 on 2011-06-21
If you go in the file manager, you can press CTRL+H, this will show all hidden files and folders.

The hidden files all contain settings. So if you delete all hidden directories, you have about the default settings for all programs. If you want to keep some settings (e.g. your firefox profile), don't delete the directory for that program.

---

### Post by Zero2Nine on 2011-06-21
> **sanderd17 said:**
> If you go in the file manager, you can press CTRL+H, this will show all hidden files and folders.

The hidden files all contain settings. So if you delete all hidden directories, you have about the default settings for all programs. If you want to keep some settings (e.g. your firefox profile), don't delete the directory for that program.

You can also rename them for example: .gconf to .gconf_old. Then a new .gconf should be created on the next login and you can still access the old folder to restore individual settings.

---

