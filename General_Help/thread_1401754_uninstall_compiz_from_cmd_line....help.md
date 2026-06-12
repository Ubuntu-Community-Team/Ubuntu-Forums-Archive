---
title: "uninstall compiz from cmd line....help"
date: 2010-02-08
forum: General Help
---

### Post by D3mon_Spawn on 2010-02-08
Hello everyone. I was recently messing around with the compiz fusion application that allows you to customize your ubuntu desktop, and while i was using it my computer froze and now every time I boot up and log in it freezes instantly and doesn't let me do anything. I figured I need to uninstall it via recovery cmd line and was just wondering how to do this...

---

### Post by Leppie on 2010-02-08
have you tried removing the compiz configuration folder?
on my system it's the ~/.config/compiz folder, but on yours it might be ~/.gconf/compiz
when you are presented with the login screen, press CTRL+ALT+F2. this will drop you to a command line login screen. enter your username and password. then issue this command:
```
mv ~/.config/compiz ~/.config/compiz.old
```
if that doesn't work, use the .gconf version:
```
mv ~/.gconf/compiz ~/.gconf/compiz.old
```
then press CTRL+F7 to return to the graphical login and see if you can login normally.

---

### Post by D3mon_Spawn on 2010-02-08
what would removing the config folder do?

---

### Post by D3mon_Spawn on 2010-02-08
> **Leppie said:**
> have you tried removing the compiz configuration folder?
on my system it's the ~/.config/compiz folder, but on yours it might be ~/.gconf/compiz
when you are presented with the login screen, press CTRL+ALT+F2. this will drop you to a command line login screen. enter your username and password. then issue this command:
```
mv ~/.config/compiz ~/.config/compiz.old
```
if that doesn't work, use the .gconf version:
```
mv ~/.gconf/compiz ~/.gconf/compiz.old
```
then press CTRL+F7 to return to the graphical login and see if you can login normally.

neither commands did the job. I think it would be better to just uninstall it. how would i do it via command line?

---

### Post by Leppie on 2010-02-08
to remove it from the command line:
```
sudo apt-get remove compiz
```however, i would still try to find the config folder first:
```
locate compiz
```

i just noticed i have a ~/.compiz as well, so it may be that folder.

---

### Post by D3mon_Spawn on 2010-02-08
Ive uninstall-ed compiz using the command above, however my computer still keeps freezing. This all started happening when I enabled the REFLECTION animations under compiz. When my computer starts up, and i log in, it looks as if its trying to perform the reflection animation then freezes the whole system. I thought that uninstalling compiz would take care of this but it is still not working. Is there a way the go into the ubuntu appearance settings and set it to NONE through the command line. If so i think this is the only thing I can try.

---

### Post by Leppie on 2010-02-08
did you search your home folder for conpiz files and folders?
```
find ~ -name *compiz
```

---

### Post by D3mon_Spawn on 2010-02-08
> **Leppie said:**
> did you search your home folder for conpiz files and folders?
```
find ~ -name *compiz
```

after searching two results come up:
~/.config/compiz and
~/.gconfig

---

### Post by 3rdalbum on 2010-02-08
At the login screen, type your name and hit enter or choose it; and then at the bottom of the screen change the session to "Gnome Failsafe". Log in. This gives you a minimal Gnome session where Compiz shouldn't be running. You can now change the Compiz settings or set visual effects to "None".

---

### Post by Robster2 on 2010-02-08
Everyone seems to be forgetting that you must switch metacity back on

code
```
sudo metacity --replace
```

that should fix your problem.

---

### Post by howefield on 2010-02-09
> **Robster2 said:**
> Everyone seems to be forgetting that you must switch metacity back on

code
```
sudo metacity --replace
```

That was mentioned in another thread the author posted, but why would you run it with sudo ?

---

### Post by Leppie on 2010-02-09
> **howefield said:**
> That was mentioned in another thread the author posted, but why would you run it with sudo ?
because he's trying to log in as root? (not the OP though)

---

