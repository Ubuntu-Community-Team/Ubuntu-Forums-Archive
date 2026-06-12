---
title: "Resolution settings"
date: 2009-11-28
forum: General Help
---

### Post by silverwood99 on 2009-11-28
Yes, ive searched the forums and followed the posts i could understand, but they didnt help me.
After installing the Nvidia driver, the resolution(4:3) at startup is quite low, and i cannot change it with the native display settings above 1024x768.
Ive read many-a-thread about this problem, and ended up having to reinstall Ubuntu because one crashed my system!
Please post a solution that goes through every step in detail, as i am quite new and only learning about commands and such...
please help!:confused:

---

### Post by pqwoerituytrueiwoq on 2009-11-28
[http://ubuntuforums.org/attachment.php?attachmentid=137959&stc=1&d=1259456400](http://ubuntuforums.org/attachment.php?attachmentid=137959&stc=1&d=1259456400)
try this command
nivida-settings

---

### Post by silverwood99 on 2009-11-28
yes, i know how to change the resolution, but it resets every login.

---

### Post by pqwoerituytrueiwoq on 2009-11-28
try it as root
mine quit working as root i think it worked before
or try logging in as root
i dont know how to in 9.10
in 9.04 system->administration->login window
or command line
gksu /usr/sbin/gdmsetup
[http://ubuntuforums.org/attachment.php?attachmentid=137961&stc=1&d=1259457313](http://ubuntuforums.org/attachment.php?attachmentid=137961&stc=1&d=1259457313)

---

### Post by silverwood99 on 2009-11-28
9.10 :( and logging in as root is quite dangerous, ive heard?
EDIT: oh, when i try to save the new settings to the Xconfig(graphically, but started in the terminal with sudo)

the terminal spits out this:
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".

```

And a dialog spits out:
```
Failed to parse existing X config file '/etc/X11/xorg.conf'!
```

---

### Post by pqwoerituytrueiwoq on 2009-11-28
it can be 
it bypasses a lot of security
 i wonder if logging in as root in text mode then starting gdm will work
reasons i use 9.04 
are 
login options 
more screen savers
boots 7 seconds faster
the theme
edit 
sudo /usr/bin/nvidia-settings
just worked for me

one good reason i use root login is updateing firefox 3 without redownloading it
if i do it with sudo changes the permissions of my app data

---

### Post by silverwood99 on 2009-11-29
Nevermind!!!!
I used the code:
```
sudo mv /etc/X11/xorg.conf ~/
```closed terminal, and in a new terminal used:

```
gksudo nvidia-settings
```

Its is working now

---

