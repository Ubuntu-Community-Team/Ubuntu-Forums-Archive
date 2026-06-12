---
title: "ATI Radeon 4200 driver install"
date: 2009-11-06
forum: General Help
---

### Post by nikola43 on 2009-11-06
the following instructions are copied from the ATI website;  my question is-exactly how do I do this?  When I'm logged in as root and copy the command it says "can't open....."--I downloaded the file to the desktop so how do I "navigate" to it?


1 Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux
  driver download.
 2 Enter the command sh ./ati-driver-installer-9-10-x86.x86_64.run to launch the ATI
  Proprietary Linux driver installer.

---

### Post by P4man on 2009-11-06
Which version of ubuntu are you using?
The recommended way is going to system > administration > hardware drivers and selecting the recommended driver. It will download and install it for you.

---

### Post by nikola43 on 2009-11-06
intrepid ibex 64

---

### Post by P4man on 2009-11-06
and the recommended driver isnt working? if you're sure you want the downloaded one then  right click the file on your desktop, properties, permissions set "allow executing file as program".

Next open a terminal. navigate to your desktop using

```
cd Desktop
```
case sensitive!

type
```

sh ./ati-
```
press TAB key to complete the name so you dont have to type everything
hit enter. follow instructions.

---

### Post by nikola43 on 2009-11-06
TNX mucho!! Problem solved!

---

