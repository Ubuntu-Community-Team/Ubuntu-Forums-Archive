---
title: "Mixed Languages"
date: 2009-12-18
forum: General Help
---

### Post by Sciamano on 2009-12-18
Hi,
I'm italian but I like to keep the operating system language as US English.
Of course I have an italian keyboard, and also I like to keep local variables (time/date, currency and so on) in the italian format.
So I've been playing a bit with locales, and currently they are as follows:

```
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=it_IT.UTF-8

```

It's more or less fine, except the fact that some applications now have menus in mixed languages.
For example, Firefox shows the menus and menu voices in english, but some extensions have italian text (Tab Mix Plus, for example).
How do I solve?
Is this related to the LC_ALL variable, which I actually don't know what it's for? :)

Thanks

---

### Post by continuous on 2011-05-25
I'm having this same problem in natty - I have some Greek and some English in the menus - pretty much all of them - firefox, banshee...
I installed the Greek language pack, set it to default, then removed it and set English (Australian) back to default. - IT's never recovered!

---

### Post by continuous on 2011-05-25
OK, I fixed it (badly)
Created a new user, saw it didn't have the problem, so I copied across all the hidden folders in the new user home directory, chowned them back to the original user and fixed.

This is fine if you have very little personalisation, but no good if you want to keep your settings...what it does do is indicate where the problem is - somewhere in the hidden folders in the home directory. My guess is gconf, but someone who knows their way around better may be able to zero in on the folder/file...

---

