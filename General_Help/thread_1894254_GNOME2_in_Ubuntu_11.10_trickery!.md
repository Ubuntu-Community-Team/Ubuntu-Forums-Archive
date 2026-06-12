---
title: "GNOME2 in Ubuntu 11.10 trickery!"
date: 2011-12-12
forum: General Help
---

### Post by JazzPotato on 2011-12-12
I thought today:
"I'd rather like to have GNOME2 back, like in maverick"

 And i settled on choosing GNOME3's fallback. After having a look in lightDM's environment menu thingy, I saw "GNOME classic" and "GNOME classic 2D" as two of the entries.

 I have posted an image of me using the apparent GNOME classic, and apparently i don't have fallback installed!
 I remember having the option of using GNOME classic with natty, I didn't think oneiric had GNOME classic installed!

What sorcery is this?

---

### Post by BC59 on 2011-12-12
To install the Gnome Shell you have to run this:

```
sudo apt-get install gnome-shell
```

To install the Gnome 3-Classic run this:

```
sudo apt-get install gnome-session-fallback
```

Once installed, log out and select "GNOME" or "GNOME Classic" from the login screen.

---

### Post by sgage on 2011-12-12
> **JazzPotato said:**
> I thought today:
"I'd rather like to have GNOME2 back, like in maverick"

 And i settled on choosing GNOME3's fallback. After having a look in lightDM's environment menu thingy, I saw "GNOME classic" and "GNOME classic 2D" as two of the entries.

 I have posted an image of me using the apparent GNOME classic, and apparently i don't have fallback installed!
 I remember having the option of using GNOME classic with natty, I didn't think oneiric had GNOME classic installed!

What sorcery is this?

Not sure I'd call it trickery. Anyway, Gnome Classic works great for me. There's a sticky above that you might be interested in - "Getting back to Gnome Classic".

---

