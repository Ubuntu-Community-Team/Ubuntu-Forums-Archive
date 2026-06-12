---
title: "Update error"
date: 2010-04-30
forum: General Help
---

### Post by ubunterooster on 2010-04-30
In update manager I get ```
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
``` :?:??

EDIT: I am using Debian in case you noticed by the screenshot but the solution should be the same as it would be if the OS was Ubuntu.

---

### Post by wojox on 2010-04-30
Edit your /etc/apt/sources.list and comment out the CD.

---

### Post by ubunterooster on 2010-04-30
"comment out"?

---

### Post by wojox on 2010-04-30
Put a # sign in front of those lines for the CD.

---

### Post by ubunterooster on 2010-04-30
No difference :(

---

### Post by wojox on 2010-04-30
Post you sources.list up here.

---

### Post by ubunterooster on 2010-04-30
# 
# deb cdrom:[Debian GNU/Linux 5.0.1 _Lenny_ - Official i386 DVD Binary-1 20090413-00:33]/ lenny contrib main

# deb cdrom:[Debian GNU/Linux 5.0.1 _Lenny_ - Official i386 DVD Binary-1 20090413-00:33]/ lenny contrib main

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main non-free contrib
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main non-free contrib

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) lenny/volatile main contrib
deb-src [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) lenny/volatile main contrib

---

### Post by wojox on 2010-04-30
That's weird. I run Lenny as a server:

```

wojox@wojox-server:/etc/apt$ cat sources.list
# 
# deb cdrom:[Debian GNU/Linux 5.0.4 _Lenny_ - Official i386 NETINST Binary-1 20100201-16:45]/ lenny main

#deb cdrom:[Debian GNU/Linux 5.0.4 _Lenny_ - Official i386 NETINST Binary-1 20100201-16:45]/ lenny main

deb http://ftp.gtlib.gatech.edu/debian/ lenny main
deb-src http://ftp.gtlib.gatech.edu/debian/ lenny main

deb http://security.debian.org/ lenny/updates main
deb-src http://security.debian.org/ lenny/updates main

deb http://volatile.debian.org/debian-volatile lenny/volatile main
deb-src http://volatile.debian.org/debian-volatile lenny/volatile main


```

If you open a terminal and run 

```
sudo apt-get update && sudo apt-get upgrade
```

Still the same? You don't have the DVD in the drive do you?

---

### Post by ubunterooster on 2010-04-30
Cd is on the desk in front of me and out of the computer

---

### Post by wojox on 2010-04-30
Well the terminal says your fine. Don't know why update-manager is giving you a hard time. It's not looking for your CD now. 

I'm gui-less being it's a server. I'm out of options. Maybe a reboot?

---

### Post by ubunterooster on 2010-04-30
It is the first boot so that kind of does make sense. (I wish I had regular Firefox...)

---

### Post by ubunterooster on 2010-04-30
Reboot does not make a difference. :(

---

### Post by wojox on 2010-04-30
> **ubunterooster said:**
> It is the first boot so that kind of does make sense. (I wish I had regular Firefox...)

I would download the newest version from Firefox.

Then unpack it:

```
tar xjf firefox-*.tar.bz2
```

Then move it:

```
sudo mv firefox /opt
```

Then create a shortcut in alacarte or main menu.

---

### Post by ubunterooster on 2010-04-30
Thanks. I think I feel like retreating  back to xubuntu for a while. I'll retry DEbian later, though

---

