---
title: "remote desktop to another computer AFTER RESTART using vinagre?"
date: 2010-11-07
forum: General Help
---

### Post by unebaguettesvp on 2010-11-07
Hi-

I have a fresh install of Ubuntu 10.10 on a home server. I can connect to it using vinagre from another computer just fine. However, if I restart the server I can no longer vnc to it because I need to log in (start a gnome session). Is there a way to do this using just vinagre? Do I need to install another vnc server on my home server? The problem is that I don't want to carry a monitor from another room just so I can log in and start a gdm session if the home server gets restarted. Thank you for your help!

---

### Post by unebaguettesvp on 2010-11-07
I figured out the answer. I used this page for help:

[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)

I edited /etc/gdm/Init/Default but I could not find gdm.conf so I didn't do that step. Instead, I saw the last comment and that worked perfectly. I had to

sudo vino-preferences

and do the same thing I did with the main user account.

---

