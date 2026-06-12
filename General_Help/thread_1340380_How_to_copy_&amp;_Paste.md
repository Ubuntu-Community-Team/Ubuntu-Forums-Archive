---
title: "How to copy &amp; Paste ?"
date: 2009-11-28
forum: General Help
---

### Post by lovemylady on 2009-11-28
[COLOR=Magenta]Hey aLL


I would like to know how to copy and paste a folder (as root!)
Why?

Cause I'd like to copy my website into my htdocs (using xampp atm :p)

(My folder is called    mywebsite)

so 

sudo cp mywebsite  etc..  doesn't seem to work  (operant is missing or so)

would be thanks for any help..[/COLOR]

---

### Post by shaggy999 on 2009-11-28
I think you need to use the -R flag when copying a folder. so:

```
sudo cp -R folder_name destination
```

---

### Post by shaggy999 on 2009-11-28
If you want to do this graphically you need to run nautilus as root using:

```
gksudo nautilus
```
Then just right-click copy, navigate to folder and right-click paste.

---

### Post by lovemylady on 2009-11-28
[COLOR=Magenta]Thanks worked perfect!
And the point with the graphically thing oh well i do not need it, was nice form you but useless ^^ thanks![/COLOR]

---

### Post by RJ12 on 2009-11-28
If this is solved you might want to mark this as "solved"


Go to the first post and click thread tools and click "Mark as solved"

---

