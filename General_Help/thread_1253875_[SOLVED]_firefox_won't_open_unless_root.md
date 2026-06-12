---
title: "[SOLVED] firefox won't open unless root"
date: 2009-08-30
forum: General Help
---

### Post by pythonscript on 2009-08-30
I installed a command line only ubuntu, followed by xorg, x-window-system-core, and icewm. I didn't like always starting the x server with sudo startx (didn't like running ALL my apps as root) so I installed slim as a login manager. However.... when I log in as myself now, I can only run firefox by "sudo firefox" at the terminal. firefox at the terminal, menu links, www link in ice's bottom panel, etc, don't do anything. They just sit there. Any ideas? I really do NOT want to be browse the web as root; that seems oddly like the flawed windows security model. Thanks!

---

### Post by Liolikas on 2009-08-30
You did something wrong for sure.., but what? Messed thing with slim I think.
sudo startx?
Just startx as simple user is enough. That may be the problem.

If you do not like type it just add it to Ubuntu equivalent of:
~/.bash_profile
~/.dash_profile I think it is. If you write command into it command will be entered after login.

---

### Post by aysiu on 2009-08-30
**Never** run the command *sudo firefox*

To fix this, close Firefox, and enter this command in the terminal: ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

Then read this so you never have a problem like this again in the future:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2009-08-30
**Never** run the command *sudo firefox*

To fix this, close Firefox, and enter this command in the terminal: ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

Then read this so you never have a problem like this again in the future:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by pythonscript on 2009-08-30
Thanks! That did exactly what I needed. Won't be making that mistake anytime soon.

---

