---
title: "zoom preferances opera browser"
date: 2011-10-04
forum: General Help
---

### Post by tobythedog on 2011-10-04
hi i want to set the default zoom on my opera browser to 160%,the list one can select in preferances has only 150% then it jumps to 180 i want 160, anyone any idea how i can get this please

---

### Post by TeoBigusGeekus on 2011-10-05
Open the ~/.opera/operaprefs.ini file (not while opera's running).
Under the [User Prefs] tag, find the Scale=100 variable and change it to Scale=160.
Save, exit, launch opera, post us what happened.

---

### Post by stinkeye on 2011-10-05
> **TeoBigusGeekus said:**
> Open the ~/.opera/operaprefs.ini file (not while opera's running).
Under the [User Prefs] tag, find the Scale=100 variable and change it to Scale=160.
Save, exit, launch opera, post us what happened.
hi TeoBigusGeekus,
You can also do this  by entering
```
opera:config
```in the addressbar and searching for **scale**.
Click the save button after altering under the **User Prefs** heading.

You may also be interested in these custom zoom buttons.
[**_[COLOR="DarkRed"]TTT-Buttons[/COLOR]_**]("http://homepage.hispeed.ch/ttt-o/button/h-bu-browserview-adv2.html")
There is one for **click:zoom to 160%, hold:zoom to 100%**

---

### Post by TeoBigusGeekus on 2011-10-05
Good to know, thanks.

---

### Post by tobythedog on 2011-10-06
graet the opera config worked a treat

---

