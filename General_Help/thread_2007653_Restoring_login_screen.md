---
title: "Restoring login screen"
date: 2012-06-21
forum: General Help
---

### Post by raysa on 2012-06-21
My computer with xubuntu 12.04 automatically logs me in at boot. I want to change this because someone else will be using the computer, so I'd like the login screen to appear at start-up. The help document says this can be done at applications>system>login screen, but when I go to applications>system there is no 'login screen' shown. How can I access this option?
Thanks, Ray

---

### Post by ryanyeah on 2012-06-21
It's under "User Accounts" if you are using 12.04

---

### Post by raysa on 2012-06-21
I have a "Users and Groups" but not a "User Accounts" that I can see. Under "Users and Groups" it gives me options for adding and deleting users but I can't see any mention or link to login screen options.

Searched through all menus and still can't find a way to change login screen settings. Is there perhaps a simple command line approach I could use?

---

### Post by LewisTM on 2012-06-21
The help you got so far pertains to Ubuntu, not Xubuntu.
Execute this command:
```
sudo leafpad /etc/lightdm/lightdm.conf
```
And remove references to autologin, then save the file.

Cheers!

---

### Post by steeldriver on 2012-06-21
see here

[http://www.liberiangeek.net/2012/03/automatically-login-to-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/automatically-login-to-ubuntu-12-04-precise-pangolin/)

do the opposite ;)

---

### Post by raysa on 2012-06-21
Fixed - thank you very much.
:D

---

