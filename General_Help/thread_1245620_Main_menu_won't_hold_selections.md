---
title: "Main menu won't hold selections"
date: 2009-08-20
forum: General Help
---

### Post by Baasha on 2009-08-20
Running Ubuntu 8.04

I recently had to do a reinstallation of my os.  I noticed the re-install of 8.04 has some items missing in the Applications menu.  The missing items are: Debian, Education, Programming, System Tools, and Universal Access.

On my old version of 8.04 all thes items showed up and each had lots of programs listed.  I went to Preferences>Main Menu and found these items listed but they were unchecked.  I tried checking them but after checking one or two the check marks disappeared, even before I could close the window.

How do I get these items back into my Applications menu?

---

### Post by zvacet on 2009-08-21
To show Debian you have to type 

```
sudo apt-get install menu menu-xdg
sudo dpkg-reconfigure menu          
sudo dpkg-reconfigure menu-xdg
```

What is other one?

---

### Post by Baasha on 2009-08-21
Ok, thanks, that got the debian menu working.  How do I get the other missing menu categories back?

---

### Post by zvacet on 2009-08-22
I´m not sure that I can help you,but what are the others?

---

### Post by Baasha on 2009-08-22
The other missing items are : Education, Programming, System Tools, and Universal Access.

I can select them in Preferences>Main Menu but after a few seconds the check marks delete themselves.

---

