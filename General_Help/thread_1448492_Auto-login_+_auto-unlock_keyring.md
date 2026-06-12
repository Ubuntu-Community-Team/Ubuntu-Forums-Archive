---
title: "Auto-login + auto-unlock keyring?"
date: 2010-04-06
forum: General Help
---

### Post by waldo000000 on 2010-04-06
Hi,

I'd like to have all of these possible at once, in Ubuntu 10.04 (Lucid):

[LIST=1]
[*]Auto-login to Ubuntu
[*]Auto-login to Google Chat and MSN (passwords saved in Empathy)
[*]An encrypted keyring (i.e. not "Use Unsafe Storage"), so that my Google & MSN passwords are not stored in clear text
[*]No need to enter a password to unlock the keyring each time I boot up
[/LIST]

Is this possible?

I have heard that it is possible to avoid having to unlock the keyring for just a *wifi connection*, by checking the "Available to all users" box for the wifi connection properties. What is the effect of this checkbox - i.e. does it store the wifi password in clear text? If not (i.e. if the wifi password is encrypted but is still somehow fully automatically unlocked), can this functionality be extended to empathy passwords?

Thanks!

---

### Post by waldo000000 on 2010-04-06
bump?

---

### Post by gadolinio on 2010-04-07
To Auto-login to Ubuntu, press Alt + F2 and type "gksu /usr/sbin/gdmsetup", then enter. It may ask for your user pwd. Go to the "security" tab, click the auto-login checkbox and put your username next to it.

---

### Post by waldo000000 on 2010-04-07
> **waldo000000 said:**
> [LIST=1]
[*]No need to enter a password to unlock the keyring each time I boot up
[/LIST]

So... I'm giving up hope. I guess the password to unlock the keyring must either be physically entered by the user (hence no auto-login), or stored in clear text somewhere (which is no better than just storing the keyring in clear text!).

I'm still intrigued as to the effect of the "Available to all users" box for network connection properties. Surely this causes  the connection password to be stored in **clear text** somewhere??

---

### Post by AP0ll0UK on 2010-04-08
I'm facing the same issue at the moment with Lucid.

I want the PC to run without the need for a mouse and keyboard to be connected, everything will be done through VNC. But I am also presented with the same message which you mentioned and can't seem to find of disabling the keyring authentication without having to store blank passwords.

> **gadolinio said:**
> To Auto-login to Ubuntu, press Alt + F2 and type "gksu /usr/sbin/gdmsetup", then enter. It may ask for your user pwd. Go to the "security" tab, click the auto-login checkbox and put your username next to it.

Is this just to configure Gnome to auto login or does it perform some other function?

Thanks.

[Edit]

Also being discussed here with reference to Lucid / 10.4 - [http://ubuntuforums.org/showthread.php?p=9093778#post9093778](http://ubuntuforums.org/showthread.php?p=9093778#post9093778)

[/Edit]

---

### Post by gadolinio on 2010-04-08
> **AP0ll0UK said:**
> 
Is this just to configure Gnome to auto login or does it perform some other function?


The window opened with that command also lets you do other things such as allowing the user root to start a GUI session, accesibility options, etc. By setting the auto login that's the only consequence i've noticed. (mmm i hope i'm actually answering your question)

---

