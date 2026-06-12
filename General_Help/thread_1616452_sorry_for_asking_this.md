---
title: "sorry for asking this"
date: 2010-11-08
forum: General Help
---

### Post by freefixkorma on 2010-11-08
hi guys i am running ubuntu 10.10 netbook everything is fine the only thing is bugging me is this keyring problem when i log in i used to log in with my password my computer passw now i have this kind of keyring everytime i am logging in please any one please give me a hand with this how do i get this out of my system and back like before with my real password ,now anyone can open my computer with this .i will appreciate any guide how to this is the message that i get thanks in advance
freefix

---

### Post by dino99 on 2010-11-08
explained there:

[http://www.ubuntu-unleashed.com/2007/08/howto-setup-guest-login-on-ubuntu-with.html](http://www.ubuntu-unleashed.com/2007/08/howto-setup-guest-login-on-ubuntu-with.html)

[http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/](http://www.psychocats.net/ubuntucat/creating-a-passwordless-account-in-ubuntu/)

---

### Post by 3Miro on 2010-11-08
This is vague. What is the actual problem. You should be asked for a password to login, only after you login, the keyring should ask you for a second password. The second password is probably for the network, so you can connect to the internet. You can go to terminal and type
```
 seahorse 
```
to manage the keyring password. (I don't know how to get to it otherwise on the netbook, it is in system -> prefs -> passwords and encryption on the desktop edition).

---

### Post by freefixkorma on 2010-11-08
i did what you mention on terminal what is next procedure it come a folder that said password
what is next thanks for your time

---

### Post by 3Miro on 2010-11-08
You have to probably enter the keyring password (whatever it is that you set it in the first place) and then you can edit a whole bunch of settings. This depends on what exactly your problem is and I still don't understand that exactly.

---

