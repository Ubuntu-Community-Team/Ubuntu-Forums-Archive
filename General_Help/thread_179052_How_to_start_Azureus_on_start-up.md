---
title: "How to start Azureus on start-up?"
date: 2006-05-18
forum: General Help
---

### Post by Prudentissimus on 2006-05-18
How do I set it to auto-run when Linux is booted?

---

### Post by dirwood on 2006-05-18
System > Preferences > Sessions > Startup Programs

add azureus.

---

### Post by theumang on 2008-05-25
What's the terminal command ?

---

### Post by theumang on 2008-05-25
Bump...

---

### Post by theumang on 2008-05-25
Doh... I tried brownse n picked the azureus.desktop file.. No Joy..
where are all the applications stored by the way and what extension do they end with ?

---

### Post by theumang on 2008-05-26
Bump (again)

is anyone else even reading my queries ?

---

### Post by soxs on 2008-05-26
azureus %F
if it won't work, try 
azureus
For future things like that, go to your gnome menu -> r-click -> edit -> go to the pending entry -> r-click -> edit -> you will see the launchcommand, which will work in most cases fine.

Edit: You usually run scripts which run the apps. The scripts should be located in /usr/bin (there are alot, use ```
 ls -Al |grep azu
``` in oder to only show commands with azu in their name)

---

### Post by crk on 2008-05-28
I think one of the following is what you need...

/usr/bin/azureus
/usr/share/menu/azureus

Good Luck!

---

### Post by soxs on 2008-05-29
/usr/bin/azureus is exactly the same as azureus :-p

---

