---
title: "I deleted some unwanted stuff (ugly themes, icons)"
date: 2009-08-14
forum: General Help
---

### Post by Couto on 2009-08-14
Well yes, I deleted the themes, and icons that I didn't like right?

Now stupid me, the icon theme I'm using relied on some of the other icon themes I guess, now I'm missing icons.

Is there a command I can do to get all the default Ubuntu 9.04 icons back?

Thank you.

---

### Post by Couto on 2009-08-14
Bump :/

---

### Post by P4man on 2009-08-14
try this:
```
sudo aptitude reinstall gnome-themes-ubuntu
```

edit: btw, 30 minutes bumps is a bit rude :/

---

### Post by Couto on 2009-08-14
> **P4man said:**
> try this:
```
sudo aptitude reinstall gnome-themes-ubuntu
```

edit: btw, 30 minutes bumps is a bit rude :/

Is this for themes or icons, or both?

Sorry my thread got buried to 2nd page and I figured nobody would even look there :/


EDIT: This is for themes, do you know the command for Icons? They're more important to me but this command did help me with the themes!

---

### Post by P4man on 2009-08-14
sudo aptitude reinstall human-icon-theme tango-icon-theme tangerine-icon-theme

not sure which other one's are there by default, but that should get you started.

---

### Post by Couto on 2009-08-14
> **P4man said:**
> sudo aptitude reinstall human-icon-theme tango-icon-theme tangerine-icon-theme

not sure which other one's are there by default, but that should get you started.

I have the human, tangerine, because I kept them, I didn't gain the tango theme.

Other themes are GNOME, and I think thats the one that its depending on for some of its icons.

sudo aptitude reinstall gnome-icon-theme?

---

### Post by P4man on 2009-08-14
yep indeed.

---

### Post by Couto on 2009-08-14
> **P4man said:**
> yep indeed.

Fixed! Thank you. :)

---

### Post by P4man on 2009-08-14
btw, if you're looking for some really nice themes:

[http://www.bisigi-project.org/?page_id=6&lang=en](http://www.bisigi-project.org/?page_id=6&lang=en)

(thanks to whomever it was that pointed me there :) )

---

