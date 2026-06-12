---
title: "one click shutdown"
date: 2009-09-27
forum: General Help
---

### Post by shaon3343 on 2009-09-27
[SIZE=4]hi there, 
  I'm using Ubuntu 9.04 . Can anyone help me for creating a one click shutdown button or creating a keyboard shortcut which would shutdown my system  immediately. :confused:  please help!
                                                                                  shaon
[/SIZE]

---

### Post by kerry_s on 2009-09-27
first you need to set it up to not need a password.

in terminal:
**sudo visudo**

put:
**your-login-name ALL=NOPASSWD:  /sbin/shutdown**

once you have that, you can use this command:
**sudo shutdown -h now**

---

### Post by LoloftheRings on 2009-09-27
follow kerry_s' instructions, and for a keyboard shortcut, go to *System* -> *Preferences* -> *Keyboard* *shortcuts* and press the *Add* button.

Name: **Shutdown**
Command: [B]sudo shutdown -h now

[/B]Press *Apply *and click the new shortcut under *Custom Shortcuts *once.
Now press your preferred shutdown shortcut, I would use a shortcut with 3 keys, so you won't press the shutdown binding by accident.

---

### Post by shaon3343 on 2009-09-27
[COLOR=Red][B]hi kerry 
    I did what you told me but it is not working! Please help me! I have included the screenshot at: 
 [http://picasaweb.google.com/charleseswain/Prof#5386110560488356322](http://picasaweb.google.com/charleseswain/Prof#5386110560488356322)
                                         shaon    [IMG]http://picasaweb.google.com/charleseswain/Prof[/IMG]
[/B][/COLOR]

---

### Post by kerry_s on 2009-09-27
> **shaon3343 said:**
> [COLOR=Red][B]hi kerry 
    I did what you told me but it is not working! Please help me! I have included the screenshot at: 
 [http://picasaweb.google.com/charleseswain/Prof#5386110560488356322](http://picasaweb.google.com/charleseswain/Prof#5386110560488356322)
                                         shaon    [IMG]http://picasaweb.google.com/charleseswain/Prof[/IMG]
[/B][/COLOR]

okay, i think it's to far up, suppose to be the last line, but make it like this instead:

[B]%admin ALL=(ALL) ALL
%admin ALL=NOPASSWD: /sbin/shutdown[/B]

---

### Post by shaon3343 on 2009-09-28
[B][COLOR=Red]heyyy kery , 
    thankssssssss a lot !!! It really works after doing that!!! thanks buddy![/COLOR][/B] :)

---

