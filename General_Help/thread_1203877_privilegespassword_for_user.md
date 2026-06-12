---
title: "privileges/password for user"
date: 2009-07-03
forum: General Help
---

### Post by jareddlc on 2009-07-03
I have a clean install of ubuntu 9.04 and i will to disable password asking(wifi, terminal,etc), or entering it once and letting it stay of entire session. to only way i could do this is logging in as root, and since i cannot autologin as root well i would like any suggestions. please explain in detail since i am still very new to linux.

---

### Post by Boondoklife on 2009-07-04
Are you refering to the elevated rights or to the keyring? The wifi bit is the keyring and setting the network to usable by all will stop that. As far as the elevated rights, why would you want to be root? This is one of the major flaws in windoes!

For a terminal bypass you can look into sudoers

---

### Post by Bucky Ball on 2009-07-04
Yes, there is a way, damn, on my Xubuntu machine at the moment so can't remember it, but it is under one of the options I think in Admin. We use it on my wife's computer; you boot up, choose a kernel and you don't need to login, is automatic. That is what you mean, right?

I'll have a look in awhile but trust me; the option is there and can be done and we do it!

This, of course, only lets you by pass logging in at boot, NOT inputting your password for changing the system.

---

### Post by jareddlc on 2009-07-04
Hello and thx, i am not concern about security, i just like to be able to access everything and modify at will. and yes i would like an autologin for root or to be able to change my current user so i can edit files under the file system since the files belong to root i cannot edit files for patching drivers etc.

---

### Post by jocko on 2009-07-04
> **jareddlc said:**
> Hello and thx, i am not concern about security, i just like to be able to access everything and modify at will. and yes i would like an autologin for root or to be able to change my current user so i can edit files under the file system since the files belong to root i cannot edit files for patching drivers etc.
It looks like you want something called "microsoft windows". You can buy it anywhere.

What you are asking for is possible, but not very clever. Plus it's against the forum's policy to tell anyone how to activate root login (so root auto login would be damn right forbidden). If you really want it I'm sure you can find it on google.

For the wifi password: Just set the keyring password to the same as your normal login password and disable autologin. That way you'll never have to enter the keyring password, as it will actually be entered when you log in to gnome.
There is a way to [change the sudo/gksudo timeout]("http://linuxowns.wordpress.com/2008/10/21/change-gksudo-timeout/").

---

### Post by t0p on 2009-07-04
> **jareddlc said:**
> since the files belong to root i cannot edit files for patching drivers etc.

Yes you can!  In the terminal, prefix your commands with [b]sudo[/i], ie

```
sudo nano /etc/avahi/hosts
```

If you want to do something as root via the gui, hit Alt+F2.  A box will appear - type in the program that you want to use as root, prefixed with **gksudo**, eg

```
gksudo nautilus
```

Now type in your password, and a new file manager window will open.  This new file manager window has admin privileges, so you can edit files owned by root with no difficulty.

Just backup any system file you want to edit, so if you screw up there's the backup to prevent your system dying. And make sure you close this nautilus window when you've finished what you're doing.

---

### Post by jareddlc on 2009-07-04
> **t0p said:**
> Yes you can!  In the terminal, prefix your commands with [b]sudo[/i], ie

```
sudo nano /etc/avahi/hosts
```

If you want to do something as root via the gui, hit Alt+F2.  A box will appear - type in the program that you want to use as root, prefixed with **gksudo**, eg

```
gksudo nautilus
```

Now type in your password, and a new file manager window will open.  This new file manager window has admin privileges, so you can edit files owned by root with no difficulty.

Just backup any system file you want to edit, so if you screw up there's the backup to prevent your system dying. And make sure you close this nautilus window when you've finished what you're doing.

thx this is very helpful. i dont get why other people are hating, im making an effort to learn.

---

### Post by Old_Grey_Wolf on 2009-07-04
> **jareddlc said:**
> thx this is very helpful. i dont get why other people are hating, im making an effort to learn.

No one is hating. It is not considered a good thing to bypass sudo or run as root. If you know enough to run unprotected then you know enough to figure out how to do it yourself without any help, IMHO. :)

---

