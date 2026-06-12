---
title: "gnome doesn't start anymore"
date: 2006-05-25
forum: General Help
---

### Post by chloraldo on 2006-05-25
GNOME doesn't start anymore. The partition where / is mounted is 100% full. I can only start with a terminal.

The partition is over 7 GB but it's full. home is on a separate partition. Any ideas what to do?

I have both GNOME and KDE installed. I don't use KDE, just some KDE programs.

Can i uninstall KDE without losing those KDE programs? How?

Thanks!

---

### Post by bruce89 on 2006-05-25
Do this to free up some HD space
```
sudo apt-get clean
```

---

### Post by aysiu on 2006-05-25
[QUOTE=chloraldo]
Can i uninstall KDE without losing those KDE programs? How?[/QUOTE] In addition to Bruce89's suggestion, you can also just [uninstall KDE](http://www.ubuntuforums.org/showthread.php?t=96048) and then reinstall only the programs you want.

Uninstalling the programs and reinstalling them will be the same as keeping them, as the configuration files and preference files do not get deleted.

---

### Post by johnc4510 on 2006-05-25
bruce89, what does that command do exactly?

---

### Post by aysiu on 2006-05-25
It removes all the .deb packages from the /var/cache/apt/archives directory.

These installer packages were originally need to install the applications you have, but now they're just sitting there.
It's like having a folder full of setup.exe files in Windows.

---

### Post by johnc4510 on 2006-05-25
Thanks aysiu

---

### Post by chloraldo on 2006-05-25
[QUOTE=bruce89]Do this to free up some HD space
```
sudo apt-get clean
```[/QUOTE]
It still doesn't work.

I get this message:
"This is the failsafe xterm session. You will be logged into a terminal console so that you may fix your system if you cannot log in any other way. To exit the terminal emulator, type 'exit' and an enter into the window."

I just don't know what to do to "fix my system"...?

Any ideas? Thanks!

---

### Post by ingo on 2006-05-25
log in on the command line and type

startx

that should start gnome cos you should have enough space now - report back please, especially in case of success :)

---

### Post by chloraldo on 2006-05-25
[QUOTE=ingo]log in on the command line and type

startx

that should start gnome cos you should have enough space now - report back please, especially in case of success :)[/QUOTE]

sorry, no success...

```
/usr/bin/startx: line 133: cannot create temp file for here document: No space left on device
... line 151 ...
... line 151 ...

X: user not authorized to run X server, sborting.
Couldn't get a file descriptor referring to the console

```

---

### Post by ingo on 2006-05-25
strange, shove a knoppix or kanotix in and check the 

 /var/cache/apt/archives 

directory on your hard drive. has it really been cleaned? If all else fails follow aysiu's instruction with apt-get:
[html]
you can also just uninstall KDE and then reinstall only the programs you want.

Uninstalling the programs and reinstalling them will be the same as keeping them, 
as the configuration files and preference files do not get deleted.[/html]

---

