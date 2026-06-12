---
title: "Startup Applications (using terminal)?"
date: 2010-09-14
forum: General Help
---

### Post by GrantStoner on 2010-09-14
I'm wondering how I would add an application to startup by using the terminal. Currently I'm using Back|Track 4, but it's based on Ubuntu, so it should be the same. However, Back|Track has no GUI for startup applications. From what I understand, it has something to do with /etc/init.d right? Sorry for posting a Back|Track question in the Ubuntu Forums. The moderators at BT are real assholes and I will never sign up to use their forums. Thanks in advance! :)

---

### Post by ajgreeny on 2010-09-14
Either make a new launcher for the application, or use a currently available launcher, ie a ***application*.desktop** file and copy it to ~/.config/autostart.  The bit I'm not sure about is making a new launcher in terminal, so you will need to search for that.

---

### Post by GrantStoner on 2010-09-14
Is there a way I can add "Startup Applications" with the GUI into the menu? What's in Ubuntu that was stripped out of Back|Track?

---

### Post by ajgreeny on 2010-09-14
Sorry, but I think I may have misunderstood your problem, and I will admit that I have no idea what Back|Track is, so can't help any more, I'm afraid.

Enlighten me a bit, please; is Back|Track a cli distro, or a desktop environment on top of Ubuntu, in the same way you would add KDE?

OK, ignore that bit, I've just googled for it and see it's a security distro.  It appears to have a GUI, so I imagine there must be a way to add startup programs some way or other.  Why not use their forum; it may be quicker.

---

### Post by GrantStoner on 2010-09-14
Their devs and forum moderators are true assholes. I will never post a question on the Back|Track forums. They make a superior distro, but their support is awful. Thanks for the help though. I'll keep researching.

---

### Post by drewsus on 2010-11-09
I just wrote a quick test script and it works. So, modifying below, you can do what you want to achieve. 

```
#!/bin/bash

#testing making a startup application

echo "
[Desktop Entry]
Type=Application
Exec=notify-send success
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_CA]=This is a Test
Name=This is a Test
Comment[en_CA]=
Comment=" > ~/.config/autostart/test.desktop
```

---

### Post by Hippytaff on 2010-11-09
> **drewsus said:**
> I just wrote a quick test script and it works. So, modifying below, you can do what you want to achieve. 
 
```
#!/bin/bash
 
#testing making a startup application
 
echo "
[Desktop Entry]
Type=Application
Exec=notify-send success
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_CA]=This is a Test
Name=This is a Test
Comment[en_CA]=
Comment=" > ~/.config/autostart/test.desktop
```
 
Excellent script, one thing though, I thinkb Backtrack might use KDE?

---

### Post by sisco311 on 2010-11-09
> **Hippytaff said:**
> Excellent script, one thing though, I thinkb Backtrack might use KDE?

So? It should work with KDE and any freedesktop.org compliant DE. 

[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

BTW, in bash I prefer to use *here documents*:
```
cat << EOF >> path/to/file
[Desktop Entry]
whatever
and so on
EOF
```
```
man bash | less +/"Here Documents"
```

---

### Post by Hippytaff on 2010-11-09
> **sisco311 said:**
> So? It should work with KDE and any freedesktop.org compliant DE. 
 
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
 
BTW, in scripts I prefer to use *here documents*:
```
cat << EOF >> path/to/file
[Desktop Entry]
whatever
and so on
EOF
```
```
man bash | less +/"Here Documents"
```
 
Fair enough - just though this part
```

X-GNOME-Autostart-enabled=true

```
might confuse things.

---

### Post by sisco311 on 2010-11-09
I think, unless OnlyShowIn or NotShowIn specifies otherwise, the app is started in any DE.

---

### Post by drewsus on 2010-11-09
I don't have Kubuntu (or any other KDE distro) but Im sure the easiest way would be to check the difference in the *.desktop files there and apply those to the above script (or one modified as sisco311 showed).

---

