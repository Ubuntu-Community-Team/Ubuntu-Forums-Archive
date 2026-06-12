---
title: "Error installing Mupen 64 Plus"
date: 2010-02-06
forum: General Help
---

### Post by Rusty103 on 2010-02-06
Everytime I try to install Mupen 64 Plus I get:

root@user-desktop:/home/daren# sudo '/home/daren/Videos/mupen64plus-bundle-bin-64-1.99.1/install.sh' 
Installing Mupen64Plus Binary Bundle to /usr/local
install: cannot stat `libmupen64plus.so.2.*': No such file or directory

Can anyone help?

---

### Post by Rusty103 on 2010-02-06
Please help, I've been trying to get it work for 3 days.

---

### Post by Luke Loughead on 2010-02-06
I'm having the same problem here. It's strange, since I have two objects matching that filename:

libmupen64plus.so.2 (a directory)
libmupen64plus.so.2.0.0 (a file)

Anyone have any ideas?

---

### Post by Luke Loughead on 2010-02-06
I did it!

The install script didn't like running with sudo, so I did

```
sudo su
```

first and then did ./install.sh in the unpacked directory. Knew it had to be something simple.

Now to take this for a spin...

---

### Post by Rusty103 on 2010-02-06
Double post sorry. Look down.

---

### Post by Rusty103 on 2010-02-06
Wait, Like this?

```
sudo su /home/user/eg/mupen64plus-bundle-bin-64-1.99.1/install.sh 
```'Cause I'm getting -

```
Unknown id: /home/user/eg/mupen64plus-bundle-bin-64-1.99.1/install.sh
```

Oh, Darn. Double post. Sorry.

---

### Post by Luke Loughead on 2010-02-06
No, do ```
sudo su
``` first. Then run the script on a separate line. "sudo su" gives you root access so that any subsequent command is run as root. The script wants a root terminal, so that's what I gave it.

---

### Post by Rusty103 on 2010-02-06
Darn it, Still getting ```
install: cannot stat `libmupen64plus.so.2.*': No such file or directory
```Even as a root.

I'm thinking it's libstdc++5 related.

Where did you get your Mupen64 from?

---

### Post by Rusty103 on 2010-02-06
I have 9.10, From what I heard you need libstdc++5 to install this properly. 9.10 has a upgraded one that doesn't work with this install correctly. 

Does anyone have a .deb of Mupen 64 plus?

---

