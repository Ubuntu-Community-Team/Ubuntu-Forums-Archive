---
title: "Cannot sign in as root."
date: 2010-11-14
forum: General Help
---

### Post by yousifmagdi on 2010-11-14
I was using windows xp, then I've installed ubuntu using the [windows installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") that ubuntu.com offers.
Before the installation begins, the program first asked me about the user name and the password that I want to set. but nothing about the root password.
Later when i tried to sign in as the root, the password i've provided didn't work for the root, but it works with my normal user name.
So now I want to sign in as a root, please help.

---

### Post by CharlesA on 2010-11-14
The root account is disabled by default in Ubuntu. You use sudo to do administrative tasks.

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yousifmagdi on 2010-11-14
From the link:
> when you run GUI programs that require root privileges (e.g. the network  configuration applet), use graphical sudo and you will also be prompted  for a password (more below).  Just remember, when sudo asks for a  password, it needs **YOUR USER password**, and not the root account password. 
is that mean to use (sudo) as a username when I login, because it didn't wok.

---

### Post by Verbeck on 2010-11-14
> **yousifmagdi said:**
> From the link:

is that mean to use (sudo) as a username when I login, because it didn't wok.

no, it means to put sudo in front of a command if you ever need to run it as root.
but for graphical applications use gksudo instead.


example: to run gedit as root, login to your normal account, open the run dialogue (alt+F2) and type, gksudo gedit  (you can also do it from the terminal)

---

### Post by coffeecat on 2010-11-14
> **yousifmagdi said:**
> From the link:

is that mean to use (sudo) as a username when I login, because it didn't wok.

No, log in as yourself. Then use sudo for terminal work or gksu/gksudo **from the terminal** for graphical apps that you need to run as root - just as it explains in that link.

Why do you think you need to log in as root?

---

### Post by nlsthzn on 2010-11-14
Coming from most other Distro's it is natural to have a root account and to use it... but I do like Ubuntu's way in this, SUDO all the way :)

---

### Post by yousifmagdi on 2010-11-14
Ok guys, I got the idea. But I was trying to login as a root to see how the source code is written for many program using the gedit editor, but even running gedit under sudo won't do the trick!!!

---

### Post by aeronutt on 2010-11-14
Hmmm...can you give an example of a file you're trying to look at?

---

### Post by Monotoko on 2010-11-14
```
sudo gedit /path/to/file
```

should do the trick :)

---

### Post by yousifmagdi on 2010-11-14
/bin/ls for example.

---

### Post by WorMzy on 2010-11-14
Most applications are compiled. You cannot simply open them in a text editor to see their code whether you're logged in as root or not. If you want to obtain the source code for an application, enable source code under System -> Administration -> Software Sources (I think), then open a terminal and run

```
apt-get source <PACKAGE NAME>
```

e.g.

```
apt-get source gedit
```

---

### Post by coffeecat on 2010-11-14
> **yousifmagdi said:**
> Ok guys, I got the idea. But I was trying to login as a root to see how the source code is written for many program using the gedit editor, but even running gedit under sudo won't do the trick!!!

What happens? Give us some details and we can help. And don't use 'sudo gedit'. Use 'gksudo gedit' - see the link that CharlesA posted for why.

> **Monotoko said:**
> ```
[SIZE=6][COLOR=Red]gk[/COLOR][/SIZE]sudo gedit /path/to/file
```should do the trick :smile:

Fixed that for you. :wink:

---

### Post by aeronutt on 2010-11-14
Ahhh...yea...eveything in /bin is binary, it's been compiled. No source. So text editors no workie.

---

### Post by Monotoko on 2010-11-14
Any files in bin are binary files, and cannot be viewed using gedit. However, the source will be in the ubuntu source.

---

### Post by Monotoko on 2010-11-14
> **coffeecat said:**
> 

Fixed that for you. :wink:

Indeed, that is twice in two days I have done that, thank you :)

---

### Post by yousifmagdi on 2010-11-14
Thanks guys for helping, I will leave the source viewing when i get expert in linux, because I'm a new user.

---

### Post by Verbeck on 2010-11-14
for gedit:
[http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.91/](http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.91/)

---

