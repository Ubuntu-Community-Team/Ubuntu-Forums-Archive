---
title: "Autostart for all users"
date: 2011-09-15
forum: General Help
---

### Post by sptutusukanta on 2011-09-15
I have some scripts & applications which I need to be **automatically started when any user (may be newly created) logged in**. It should **reflect all users** not only mine!

I mean, I want to put my scripts & applications to the **global startup location**. Where is it?

***I don't want to install any app*** to accomplish this.
***Actually I want to know how UBUNTU does it***.

---

### Post by haqking on 2011-09-15
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

probably  /etc/rc.local is what you are looking for

---

### Post by sptutusukanta on 2011-09-15
I want the application **DOCKY** to be automatically started. It has a settings to for autostart after login. But, It has to be started at** least once** by the **new user**.

This can be solved by ***init*** or ***init.d*** I think.
But it will create another problem, as it will **regain its own default settings**. Is it possible to **make a default settings for all users**?

Please Help!!

---

### Post by sptutusukanta on 2011-09-15
> **haqking said:**
> [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

probably  /etc/rc.local is what you are looking for

I'm new to this. So, can't understand all the stuff written there.
I think **init** & **init.d** are startup ***before*** login. I want to do it ***after*** login of any user.

---

### Post by Azdour on 2011-09-15
Hi,

I'm not sure if there is a better way but I would:

Write a script to place a file into every users /config/autostart directory. (You would have to rerun the script as you add new users)

This file is a .desktop file - basically a launcher. This will launch a script that runs the commands you want to run.

Any .desktop file in /config/autostart is run when the users logins.

---

### Post by staticd on 2011-09-15
You could try putting stuff in the files in /etc/gdm.

I think the Xsession file is the one to edit.

The Arch linux wiki has a very good explanation if I remember correctly.

---

### Post by WorMzy on 2011-09-15
Generally, .desktop files in /etc/xdg/autostart/ are launched when X starts no matter which user logs in. It seems to depend on the desktop environment though; openbox has it's own autostart file under /etc/xdg/openbox/autostart, in which applications have to be written down like
```
xfce-mcs-manager &
clipit &
#etc
```

---

