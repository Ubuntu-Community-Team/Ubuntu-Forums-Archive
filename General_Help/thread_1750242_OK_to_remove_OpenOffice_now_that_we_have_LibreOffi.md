---
title: "OK to remove OpenOffice now that we have LibreOffice?"
date: 2011-05-05
forum: General Help
---

### Post by Fraoch on 2011-05-05
I noticed there were updates for everything related to OpenOffice today which reminded me, now that LibreOffice is the default, why keep OpenOffice?

I removed OpenOffice and all its components.  LibreOffice still runs unaffected, but now autoremove wants to uninstall LibreOffice as well.

Is OpenOffice a dependency of LibreOffice?  Should I reinstall OpenOffice?

---

### Post by dino99 on 2011-05-05
the autoremove script might be not updated yet, i dont have ooo anymore on my system and dont get complain at all

---

### Post by Spyderkid on 2011-05-05
```
sudo apt-get remove openoffice
sudo apt-get install libreoffice

```

That Help? :)

---

### Post by Fraoch on 2011-05-05
> **Spyderkid said:**
> ```
sudo apt-get remove openoffice
sudo apt-get install libreoffice

```

That Help? :)

So LibreOffice has to be reinstalled if OpenOffice is removed?:confused:

Or is this just to get rid of autoremove wanting to remove LibreOffice now?

---

### Post by AllGamer on 2011-05-05
that's the first thing i did to all my 10.10 installations

---

### Post by Spyderkid on 2011-05-07
what i said gets rid of openoffice and if you don't have libreoffice then you can do the second line

---

### Post by Spyderkid on 2011-05-07
and by using apt-get you should override the auto thing
(so don't use second line you'll just get an error)

or if that doesn't work use 
```

sudo apt-get --reinstall libreoffice

```

---

### Post by grahammechanical on 2011-05-07
Do not forget that Libreoffice is still using some of the libraries from Openoffice. This is a transitional period where the Libreoffice people are changing the names of the libraries from openoffice to libreoffice. Both programs use the same libraries but over time the names will be changed. So, do not be surprised to see Openoffice libraries even when Openoffice has been removed.

Regards.

---

