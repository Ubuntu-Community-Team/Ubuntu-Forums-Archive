---
title: "Firefox Namoroka problem!"
date: 2010-02-01
forum: General Help
---

### Post by cellarosi on 2010-02-01
Hello :)

I need help.
I've update firefox in a new version "Namoroka".
After that when I tried to start it, infinity firefox windows are opened on the screen.
I have to restart every times. 

If I try to start it from root the problem doesn't occured. 

Some ideas about this problem? :(

Thank you in advance.

---

### Post by raktarok on 2010-02-01
Hi,

Try deleting the hidden folder .mozilla in your home folder, and see if it works now. You will lose all your settings, history if you do this though.

---

### Post by lovinglinux on 2010-02-01
> **raktarok said:**
> Hi,

Try deleting the hidden folder .mozilla in your home folder, and see if it works now. You will lose all your settings, history if you do this though.

There is no need to do that. Most problems can be fixed without deleting the ~/.mozilla folder. But if you don't mind loosing ALL your settings, then I would recommend deleting ~/.mozilla/firefox instead.

@cellarosi

If you started Firefox using sudo (NEVER DO THAT) read [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

Then tell me how did you install Namoroka so I can have a better idea of what is going on.

---

### Post by cellarosi on 2010-02-02
Thank a lot.. 
now it works after i deleted  ./mozilla/firefox  folder. :)

---

