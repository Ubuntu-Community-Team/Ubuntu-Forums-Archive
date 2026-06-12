---
title: "no shutdown button on gnome pannel"
date: 2010-01-09
forum: General Help
---

### Post by prabhanjan2906 on 2010-01-09
I installed KDE on my ubuntu 9.04. I was using kde for some time. Then later on i switched it back to gnome. I found that the shutdown button on the right top of the gnome pannel was missing. How to restore it back? and has my gnome pannel crashed? thank you in advance!

---

### Post by Spectre5 on 2010-01-09
Right click on panel and select "add to panel."  Then find "indicator applet session" and move it to anywhere on any panel you want.

---

### Post by unmole on 2010-01-09
Just right click on where you want to add the button, choose 'Add to panel' and then select 'User Switcher' or even 'Shutdown'. If you want to restore the default gnome panel settings, do a 

```
 sudo debconf gnome-panel 
``` and then restart.

---

### Post by Quarkrad on 2010-01-09
I also have this problem.  Followed you terminal command and got:

dad@dadubuntu:~$ sudo debconf gnome-panel
[sudo] password for dad: 
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2573): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

---

