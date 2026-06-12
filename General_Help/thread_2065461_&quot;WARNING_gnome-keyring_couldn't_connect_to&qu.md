---
title: "&quot;WARNING: gnome-keyring:: couldn't connect to&quot;"
date: 2012-10-02
forum: General Help
---

### Post by peyre on 2012-10-02
The other night I tried to log into PYLOTRO, but received this message:

```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-YPU1bi/pkcs11: No such file or directory

*** Finished ***
```

If I create a blank pkcs11 file there, I get this:

```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-YPU1bi/pkcs11: Connection refused

*** Finished ***
```

I've been using PYLOTRO without any trouble for several months now.  I haven't made any big system changes that I can recall, just installed the usual Ubuntu updates.  I'm running 12.04.

---

### Post by peyre on 2012-10-04
Argh!  No one has any ideas?  (bump)

---

### Post by peyre on 2012-10-05
Bump!

---

### Post by daslinkard on 2012-10-05
I found where another person was able to beat this [here]("http://laslow.net/2012/05/06/gnome-keyring-issues-in-ubuntu-12-04/").  Good luck and let me know how this works for you.

---

### Post by jerrrys on 2012-10-05
And I been looking at this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gnome-keyring%3A%3A+couldn%27t+connect+pkcs11&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gnome-keyring%3A%3A+couldn%27t+connect+pkcs11&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by PoliticKiller on 2012-10-31
Take a look to :

[http://hongouru.blogspot.com.ar/2012/07/solved-warning-gnome-keyring-couldnt.html](http://hongouru.blogspot.com.ar/2012/07/solved-warning-gnome-keyring-couldnt.html)

Maybe help.

---

### Post by chascon on 2012-12-22
Forget editing sudo nano /etc/xdg/autostart/gnome-keyring-pkcs11.desktop (which didn't work for me) or disabling gnome's keyring service (which I find extreme).

What worked for me (running OpenBox) was adding the following line to the end of .config/openbox/autostart.sh

eval $(gnome-keyring-daemon --start) &

If you don't run OpenBox, try putting the same line in .xsession, as per comment 29 from [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/932177) I haven't tried this last fix.

---

### Post by JoshuaXD on 2013-03-22
> **PoliticKiller said:**
> Take a look to :

[http://hongouru.blogspot.com.ar/2012/07/solved-warning-gnome-keyring-couldnt.html](http://hongouru.blogspot.com.ar/2012/07/solved-warning-gnome-keyring-couldnt.html)

Maybe help.

**I'm using LXDE in Lubuntu 12.10, but the solution in this link worked for me. (Short form: ****add "LXDE;" to the "OnlyShowIn=" line of**** /etc/xdg/autostart/gnome-keyring-pkcs11.desktop and then reboot.) **

---

