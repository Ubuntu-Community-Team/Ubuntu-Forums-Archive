---
title: "kill application automatically after login"
date: 2011-01-09
forum: General Help
---

### Post by w1ll1am on 2011-01-09
Hello everyone I am using kvkbd as an onscreen keyboard and I have it set to start on the login screen but after I login I want the keyboard to close and I can not get this to work. At the bottom of  /etc/gdm/Init/Default
I added the line.

```
 exec kvkbd& 
```This works great and kvkbd starts up and even puts a panel icon at the bottom of the login screen but after the login the keyboard is still there?

I have tried making a launcher and adding it to the startup applications. I wrote a script and put it in the /usr/sbin and /usr/bin and also added a line at the bottom of my /etc/rc.local that should have run that same script to kill kvkbd and nothing. 

The really weird thing is that the launcher that I made would work if I double clicked on it but if i had it set to run as a startup application it would not work. This is driving me crazy can anyone help? thanks

---

### Post by w1ll1am on 2011-01-11
Bump

---

### Post by w1ll1am on 2011-01-25
bump

---

### Post by w1ll1am on 2011-02-03
So I am guessing no one knows how to to this?

---

