---
title: "How can I sync my root gedit with my user gedit's preferences?"
date: 2012-01-16
forum: General Help
---

### Post by winchendonsprings on 2012-01-16
When I open a file with root gedit I'd like to have the same setup as my normal gedit. So theme, preferences, and addons.

Can I set up some sym links in the right spot to achieve this?

---

### Post by Serpher on 2012-01-16
[http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

Google is your friend. Found this in under a minute after searching "GTK themes root ubuntu"

---

### Post by winchendonsprings on 2012-01-16
Not my GTK theme. My gEdit theme (color scheme), along with it's enabled plugins and preferences. So it's specific to gEdit.

---

### Post by Xgen on 2012-01-16
Well, I see that there is a gedit-2 file under ~/.gconf/apps. Create a link to that and replace the one in the root folder. Also one under ~/.conf/gedit too, if necessary.

---

### Post by winchendonsprings on 2012-01-17
> **Xgen said:**
> Well, I see that there is a gedit-2 file under ~/.gconf/apps. Create a link to that and replace the one in the root folder. Also one under ~/.conf/gedit too, if necessary.


Sounds good... Just... Where are gedit's root profile settings stored now? It doesn't look like they are in /root/.gconf/apps or /root/.config/gedit ...

---

