---
title: "Title bar  is Gone... HELP"
date: 2011-05-01
forum: General Help
---

### Post by shaka89 on 2011-05-01
I upgraded today to 11.04 (in classic mode) I tried to get the cube desktop effect, but now the title bar is gone (maximize,  minimize, close), and to make it worst, I can't access the system settings... any one knows how to fix this from the Terminal? any help is appreciated thanks

---

### Post by pqwoerituytrueiwoq on 2011-05-01
[FONT=Courier New]compiz --replace[/FONT] should do it
if not
[FONT=Courier New]metacity --replace[/FONT]

---

### Post by Finalfantasykid on 2011-05-01
better to use ALT + F2 for these

```
metacity --replace
```

or try

```
compiz --replace
```

That should bring back your title bars.  The second one might not work because maybe unity is conflicting with some of your settings, I'm not sure.

---

### Post by shaka89 on 2011-05-01
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]compiz --replace[/FONT] should do it
if not
[FONT=Courier New]metacity --replace[/FONT]
[FONT=Courier New]metacity --replace works, however if I try to close the terminal [/FONT]I get this error: There is still a process running in this terminal. Closing the terminal will kill it.
and if I click close, the terminal freezes and I can't do anything, I have to restart, and the title bar is not back :(

---

### Post by pqwoerituytrueiwoq on 2011-05-01
use alt+f2 as stated in post 3

---

### Post by shaka89 on 2011-05-01
> **pqwoerituytrueiwoq said:**
> use alt+f2 as stated in post 3
well that fixed it, alt+f2 was not working so I had to do it from the terminal and THEN use alt+f2, idk why it wasn't working, but thanks guys

---

### Post by pqwoerituytrueiwoq on 2011-05-01
probably the part of the ui that the mouse had last been active on

---

### Post by zeddock on 2011-05-19
metacity --replace
worked for me. Thanx!
Zeddock

---

### Post by zeddock on 2011-05-20
I take that back...

It fixed it until I rebooted!

Where can I make it permanent?

zeddock

---

### Post by fragos on 2011-05-20
Add metacity in the Startup Applications and you get it with every boot. What you're seeing is a bug in the online update process where for some reason metacity doesn't start. For me I had the same issue with unity and I also placed it in Startup Applications. It seemed to work after that but not being sure if anything else was missing I opted to do a clean install and all is well.

---

### Post by linuxinstalledfromhdd on 2011-05-20
just a tip - you can create a new user on Ubuntu to do the same thing

---

### Post by zeddock on 2011-05-23
Can I do a re-install?
I did an upgrade from 10 and everything is going badly.  My network-manager was not showing in notifications area and I tried to install connman as a fix...
Now I cannot get network-manager back on...  and others too....

When I go to install I get errors like...
> dpkg: warning: parsing file '/var/lib/dpkg/status' near line 13850 package 'ubuntu-tweak':
 error in Version string 'karmic-0~20101117~maverick1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 13851 package 'ubuntu-tweak':
 error in Config-Version string 'karmic-0~20101117~maverick1': version number does not start with digit


which seems like part of my system does not understand I am on 11.04!

Please help, or direct me to folks who can?  Thanx!

zeddock

---

