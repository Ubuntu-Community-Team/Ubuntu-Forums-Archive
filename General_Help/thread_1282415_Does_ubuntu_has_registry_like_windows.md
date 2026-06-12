---
title: "Does ubuntu has registry like windows???"
date: 2009-10-04
forum: General Help
---

### Post by kart168 on 2009-10-04
hello ppl!

i've installed ubuntu a few days back and totally attracted towards it. I have a doubt. Windows has a series of files called the registry which are very important to the functioning of the OS. So does ubuntu also has such thing called registry?? pls clear my doubt .

thank you.:)

---

### Post by scragar on 2009-10-04
Ubuntu doesn't have a registry, all your settings and configs are stored in plain text, user based config files are stored in your home folder(press ctrl+H to show them), system config files are stored in /etc or /var

---

### Post by pedro3005 on 2009-10-04
But GNOME has something similar, the gconf-editor. To open it press ALT+F2 and type gconf-editor.

---

### Post by kart168 on 2009-10-04
oh! now i can see the gconf-editor window thanks. even though i couldn't get anything out of it. i'll dig deep to get some knowledge on it...thanks buddy thank u very much...

---

### Post by MaxIBoy on 2009-10-04
Linux doesn't have one big registry. Individual software packages are left up to their own devices as to how they store their information, and some (Firefox and GNOME for example) use a registry design.

From what I know though, at least in GNOME the registry isn't one huge file, but a collection  of smaller files (so the computer doesn't get slower and slower as the registry grows.)


Most programs use plain old text files for configuration. Most of these files can be found in /etc. For programs where each user on the system can have his own preferences, config files can be found in your home directory as dot-files (files with names beginning in a dot are hidden.) Some will be in .config inside your home directory. 


Eric S. Raymond wrot a book, The Art of Unix Programming, which explains some of the design principals behind this:
[http://www.faqs.org/docs/artu/ch01s06.html](http://www.faqs.org/docs/artu/ch01s06.html)
[http://www.faqs.org/docs/artu/ch05s01.html](http://www.faqs.org/docs/artu/ch05s01.html)
And here is a look at the kinds of syntax you can expect when editing these files:
[http://www.faqs.org/docs/artu/ch05s02.html](http://www.faqs.org/docs/artu/ch05s02.html)

---

### Post by aysiu on 2009-10-04
> **kart168 said:**
> oh! now i can see the gconf-editor window thanks. even though i couldn't get anything out of it. i'll dig deep to get some knowledge on it...thanks buddy thank u very much...
*gconf-editor* is a graphical frontend for editing local text files.

It is also a lot less confusing than the Windows registry, and it affects only your personal settings, no system settings.

---

