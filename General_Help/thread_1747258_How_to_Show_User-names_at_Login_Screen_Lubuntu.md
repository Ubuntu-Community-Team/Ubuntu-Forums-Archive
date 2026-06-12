---
title: "How to Show User-names at Login Screen Lubuntu  ?"
date: 2011-05-02
forum: General Help
---

### Post by SILLAT on 2011-05-02
I'm Running Lubuntu 10.04 on an old P3 PC
Every time i want to log in i have to type the user-name and password.
Is there any way Lubuntu can show the user-name to the login screen so that when i reach the login screen i see the usernames an i just click on the user-name enter the password and login ?
Is that achievable in Lubuntu 10.04 ?

[COLOR="Red"]***[/COLOR]I made this post in the wrong section of the forums hence this is a double post [ i hope the moderators dont flame me too hard for my mistake..my apologies..ok]


Any Links/tutorial is welcomed

thanks in advance

---

### Post by ajgreeny on 2011-05-02
I don't think you can do it with lxdm, the default display manager for lubuntu, but you could use gdm instead by installing it and then running ```
sudo dpkg-reconfigure gdm
``` and choosing the one you want.

**gdm** is a bit more resource hungry than lxdm, I think, but it will make little difference one the GUI is running.

I have no idea if gdm will bring in masses of gnome dependencies or not, but give it a try.

---

### Post by zvacet on 2011-05-02
If you don´t want to type username & password every time then under login session select autologin and choose witch user you want to autologin to.

---

### Post by CharlesA on 2011-05-02
Merged the post from your other thread and closed it.

If you post in the wrong forum, click the "report abuse" button and ask that it be moved. Thanks. :)

---

### Post by SILLAT on 2011-05-02
> **ajgreeny said:**
> I don't think you can do it with lxdm, the default display manager for lubuntu, but you could use gdm instead by installing it and then running ```
sudo dpkg-reconfigure gdm
``` and choosing the one you want.

**gdm** is a bit more resource hungry than lxdm, I think, but it will make little difference one the GUI is running.

I have no idea if gdm will bring in masses of gnome dependencies or not, but give it a try.

@ ajgreeny - I dont have a lot of resources so i guess i'll have to leave it as it is if lxdm cannot do it.
Thanks much

@zvacet - i have more than one person using the machine so i cant select auto-login

@CharlesA - Apologies again [someone closed the thread..thanks much]

---

