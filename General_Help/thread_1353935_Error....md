---
title: "Error...???"
date: 2009-12-13
forum: General Help
---

### Post by robertcoulson on 2009-12-13
Hi...I used "Update Manager", and everything went ok, but when I hit the "Check" button, I get the "ERROR" message as seen in the attachment.....Don't know what it means...??
Thanks, Bob

---

### Post by sisco311 on 2009-12-13
You have to add Medibuntu's GPG key to your keyring, which is needed to authenticate the Medibuntu packages.

Open a terminal (Applications -> Accessories -> Terminal) 
and run:
```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
```
and
```
sudo apt-get update
```

[uhelp]community/Medibuntu[/uhelp]

---

### Post by robertcoulson on 2009-12-13
**WOW**...Thanks for the help...It worked perfectly...Don't know what I did, but it worked.
Thanks very, very much,
Bob

---

