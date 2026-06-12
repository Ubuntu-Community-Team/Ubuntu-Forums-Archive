---
title: "Can't Login"
date: 2010-11-17
forum: General Help
---

### Post by Kyluke on 2010-11-17
Hey

I just did a normal security update and now I can't login.
Why is this happening and how do I fix it?
No error messages, nothing just tries to login and then presents me with the login screen once again.
I have tried

sudo dpkg -reconfigure gdm
sudo dpkg -reconfigure gnome-session

Please help it is critical that I use my PC.

---

### Post by TeoBigusGeekus on 2010-11-17
Boot into recovery mode and when in terminal give
```
gnome-session
```
and post us any error messages.

---

### Post by io5cml4z on 2010-11-17
Probably a password problem. Boot into recovery mode from grub, use the root terminal and type:
> passwd **USER NAME HERE**
And then type your new password. If you can't access the root terminal, like me (It happened about 3 hours ago), then use a live cd and follow [these]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/") instructions.

---

### Post by Kyluke on 2010-11-18
I booted into recovery mode and when i ran gnome-session i gave me:

** (gnome-session:1233): WARNING **: Canot open display:

and it wasn't the password problem, I tried that too.

---

### Post by Kyluke on 2010-11-18
I guess reinstalling is the order of the day....

---

### Post by marks_linux on 2010-11-19
nothing much to add except 'me too'. Can't get past the login screen.

---

### Post by Kyluke on 2010-11-19
I made a backup of my entire home folder and did a reinstall and copied my home folder back and the same thing happened which leads me to think that there is some configuration file within the home folder which is the problem.

I copied only the necessary and did the reinstall again and let ubuntu recreate all the config files and everything is fine now. My suggestion if nothing else works is to just reinstall.
I ran updates and that didn't effect anything either so yeah.... For me this is unresolved yet solved

---

