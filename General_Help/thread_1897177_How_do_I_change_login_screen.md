---
title: "How do I change login screen?"
date: 2011-12-18
forum: General Help
---

### Post by xxhopingtearsxx on 2011-12-18
I'm using Ubuntu 11.10 but I also have Lubuntu and Xubuntu installed. Since I installed Lubuntu (simply to try it out), my login screen is back to the login screen from 11.04. I dislike it

How do I get the default Ubuntu 11.10 login screen back?

Also if anyone wants, I also have the Xubuntu splash when I shut down and startup my laptop.. How do I put it back to Ubuntu?

---

### Post by BC59 on 2011-12-18
I don't know if you need something like this:
[http://blog.sudobits.com/2011/10/06/how-to-change-login-screen-in-ubuntu-11-10/](http://blog.sudobits.com/2011/10/06/how-to-change-login-screen-in-ubuntu-11-10/)

---

### Post by Frogs Hair on 2011-12-18
getting back to pure Gnome . [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by xxhopingtearsxx on 2011-12-18
Solved it.
The issue was that after installing Lubuntu, my login screen wasn't the default from 11.10 that I liked, so to restore it I did:

Go to terminal
sudo -s (Not sure if needed but I did it just incase)
cd /etc/X11
sudo gedit default-display-manager
the file should have this:
/usr/sbin/lightdm
Then I restarted..

I guess I should've googled.

---

