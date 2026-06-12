---
title: "GNOME won't remember settings"
date: 2010-05-11
forum: General Help
---

### Post by johnjust on 2010-05-11
I deleted my old Mint partition and did a fresh 10.04 install, but GNOME will not remember my settings for Advanced Desktop.

Every time I login, I get windows with no borders, and I have to set Advanced Desktop again.

Any ideas?

---

### Post by GSF1200S on 2010-05-11
I dont really know why you are having this issue- it has to be something to do with compiz failing to load as the DE starts. What happens if you do:
```
compiz --replace
```
instead of enabling the advanced effects option again?

Best I can suggest, if the above command works and since I dont know or have any idea what could be causing the problem, is to create a script and have gnome run it at startup. So, for example create a simple script:
```
#!/bin/bash
sleep 3
compiz --replace
```
and save it as compiz.sh. Then, right click on the script, go to properties and then the permissions tab, and allow the file to run as a program. Move the file wherever you like. Next, go into System>Preferences>Startup Applications, click add, name it whatever you want, and then navigate (using the browse button) to the location of the script created above. This is a dirty way of fixing the problem, so if anyone else knows whats causing it, hopefully they will post here.

---

### Post by johnjust on 2010-05-11
> **GSF1200S said:**
> I dont really know why you are having this issue- it has to be something to do with compiz failing to load as the DE starts. What happens if you do:
```
compiz --replace
```
instead of enabling the advanced effects option again?


Interesting, I have the following output in the terminal:

```

justin@justin-laptop:~$ compiz --replace &
[1] 1758
justin@justin-laptop:~$ Starting gtk-window-decorator

```

Looks like the window decorator doesn't start when I boot.  Should I just add a startup item for "gtk-window-decorator"?

---

### Post by GSF1200S on 2010-05-11
> **johnjust said:**
> Interesting, I have the following output in the terminal:

```

justin@justin-laptop:~$ compiz --replace &
[1] 1758
justin@justin-laptop:~$ Starting gtk-window-decorator

```

Looks like the window decorator doesn't start when I boot.  Should I just add a startup item for "gtk-window-decorator"?

**EDIT** When you startup gnome and your window borders are missing, hit Alt+F2 and type:
```
gtk-window-decorator --replace
```
If that gives you window borders, than use:
```
gtk-window-decorator --replace
```
in place of the compiz --replace I listed above. Doesnt really matter- either way will work. I dont see why its not working when you start the desktop :/ **EDIT**

Actually, I tested it out and that should work. For good measure, use:
```
gtk-window-decorator --replace
```
You shouldnt need the --replace, but it wont hurt anything.

---

### Post by johnjust on 2010-05-11
It's actually compiz itself that doesn't seem to start.

I have my NVIDIA enabled through "Hardware Drivers", and I also installed Docky, but another reboot says I "need compositing enabled".

I can't remember if previous installs actually had Compiz on the startup list, but should I just add "compiz --replace" there?

---

### Post by GSF1200S on 2010-05-11
> **johnjust said:**
> It's actually compiz itself that doesn't seem to start.

I have my NVIDIA enabled through "Hardware Drivers", and I also installed Docky, but another reboot says I "need compositing enabled".

I can't remember if previous installs actually had Compiz on the startup list, but should I just add "compiz --replace" there?

Sorry for the delay- Yes, I would just add compiz --replace. Hopefully someone else will come along who knows WHY compiz isnt starting itself on every startup.

---

### Post by johnjust on 2010-05-12
> **GSF1200S said:**
> Sorry for the delay- Yes, I would just add compiz --replace. Hopefully someone else will come along who knows WHY compiz isnt starting itself on every startup.

No problem, I actually did it a couple minutes after I posted and it worked fine.  I'd like to find out why it's not starting, but as long as this works, it should be fine.

I don't understand why some of these things work like this.  I wiped out my old root partition, and I removed my .gconf directory when I installed 10.04 so I would start fresh - but I didn't start too fresh...

Compiz won't start (and also won't understand window classes, for losing the shadow on Conky), items in "Places" have no file type assocation with them (fixed), I was missing icons for Firefox and Ubuntu One in my menu (fixed by deleting and re-adding), and some other small problems here and there.

When I removed my Karmic partition to install Mint 8, it went perfect the _first time_.  In the past, as I've freshly installed new Ubuntu versions, I usually had to install it once or twice before it comes out perfect, maybe I just need to do it over.  The ISO checked fine, but I usually always order an official disc just to make sure.

---

