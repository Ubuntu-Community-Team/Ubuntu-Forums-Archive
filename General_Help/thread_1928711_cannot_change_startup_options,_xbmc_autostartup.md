---
title: "cannot change startup options, xbmc autostartup?"
date: 2012-02-20
forum: General Help
---

### Post by qwertyjjj on 2012-02-20
I set xbmc to startup automatically. However, when I now exit the program, it returns to the desktop but I have no options to log out, no launcher menu, no system settings.
How can I edit the startup to turn off xbmc?
I tried gksudo gdmsetup but it won't load.

---

### Post by qwertyjjj on 2012-02-21
> **qwertyjjj said:**
> I set xbmc to startup automatically. However, when I now exit the program, it returns to the desktop but I have no options to log out, no launcher menu, no system settings.
How can I edit the startup to turn off xbmc?
I tried gksudo gdmsetup but it won't load.

Any ideas?

---

### Post by stinkeye on 2012-02-21
ctrl+alt+t should give you a terminal
and then open startup preferences with
```
gnome-session-properties
```

What release are you using and what session are you logging into?

---

### Post by qwertyjjj on 2012-02-21
> **stinkeye said:**
> ctrl+alt+t should give you a terminal
and then open startup preferences with
```
gnome-session-properties
```

What release are you using and what session are you logging into?

I am just logging as the normal user, xbmc then autostarts but when I exit it, I get a desktop with no access to anything.
This is 11.10 and xbmc is the latest stable build.

I have stopped xbmc from loading but on startup now, still nothing on the desktop, I just get the file, edit, view menu on top...no launcher, no settings or dates or user log out options on the top right.

---

### Post by stinkeye on 2012-02-21
Do you normally login to unity... ie the "**Ubuntu**" session.
To check what session your in,run...
```
echo $DESKTOP_SESSION
```


What window manager is running?
To easily find out install wmctrl.
```
sudo apt-get install wmctrl
```


Then run 
```
wmctrl -m
```

eg
```
glen@Oneiric:~$ wmctrl -m
Name: **Compiz**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```


If your in the "ubuntu" session but **Metacity** is showing as your window manager (unity needs compiz),run...
```
compiz --replace & disown
```


If your in the "ubuntu" session and **Compiz** is showing as your window
manager then reset the unity plugin with...
```
unity --reset && compiz --replace & disown
```
...the "**&& compiz --replace & disown**" is not really needed but 
i find sometimes after running "unity --reset" I need to run "compiz --replace" for it to load properly.

****The commands can take 30 secs or more to run****

---

### Post by qwertyjjj on 2012-02-21
echo $DESKTOP_SESSION: ubuntu 2wd

What window manager is running?
To easily find out install wmctrl.
wmctrl -m
compiz
class n/a
pid n/a
show desktop mode off

sown[/CODE]


If your in the "ubuntu" session and **Compiz** is showing as your window
manager then reset the unity plugin with...
```
unity --reset && compiz --replace & disown
```
...the "**&& compiz --replace & disown**" is not really needed but 
i find sometimes after running "unity --reset" I need to run "compiz --replace" for it to load properly.

ran that and that fixed it but why would autostarting xbmc put it into desktop off mode?

---

### Post by stinkeye on 2012-02-21
> **qwertyjjj said:**
> echo $DESKTOP_SESSION: ubuntu 2wd

What window manager is running?
To easily find out install wmctrl.
wmctrl -m
compiz
class n/a
pid n/a
show desktop mode off

sown[/CODE]


If your in the "ubuntu" session and **Compiz** is showing as your window
manager then reset the unity plugin with...
```
unity --reset && compiz --replace & disown
```
...the "**&& compiz --replace & disown**" is not really needed but 
i find sometimes after running "unity --reset" I need to run "compiz --replace" for it to load properly.

ran that and that fixed it but why would autostarting xbmc put it into desktop off mode?

It looks like your were  in the **ubuntu 2d** session which normally
runs metacity as the window manager.

Log out and choose the "ubuntu" session by clicking on the cog icon
then log in as normal.

I think you may have been in the "**ubuntu 2d**" session but the 2d launcher and panel weren't loading. I get that in my 2d session.

At the moment your in the 2d session but have replaced the window manager
Metacity with Compiz(and with it loaded the unity 3d plugin).
So you have more or less turned it into a 3d session.

The **show desktop mode off** just refers to your **show desktop** status.
ie if you have used ctrl+alt+d to minimize all windows to show the desktop.

---

### Post by qwertyjjj on 2012-02-21
> **stinkeye said:**
> It looks like your were  in the **ubuntu 2d** session which normally
runs metacity as the window manager.

Log out and choose the "ubuntu" session by clicking on the cog icon
then log in as normal.

I think you may have been in the "**ubuntu 2d**" session but the 2d launcher and panel weren't loading. I get that in my 2d session.

At the moment your in the 2d session but have replaced the window manager
Metacity with Compiz(and with it loaded the unity 3d plugin).
So you have more or less turned it into a 3d session.

The **show desktop mode off** just refers to your **show desktop** status.
ie if you have used ctrl+alt+d to minimize all windows to show the desktop.

But what would change it? I never minimised anything.
Unless xbmc is doing it when it quits but on normal load it doesn't do that.

---

### Post by stinkeye on 2012-02-21
The normal output is **Window manager's "showing the desktop" mode: OFF**
Test it. open a terminal and run **wmctrl -m**.
Press ctrl+alt+d to show the desktop.
Then bring the terminal back up using the mouse and run **wmctrl -m** again.
It will show **Window manager's "showing the desktop" mode: ON**
Has nothing really to do with your problem and doesn't affect anything.

The problem is probably due to the fact that a build of xbmc for
oneiric is only in the unstable ppa.

---

### Post by qwertyjjj on 2012-02-22
When I select shutdown or restart now from the desktop, it doesn;t do that it just logs me off.
 To restart I have to open a terminal and do sudo reboot.

Also, unity --reset& works in the current session but when I restart, it disappears again.

---

### Post by stinkeye on 2012-02-22
When your at the logon screen make sure you choose Ubuntu as the session
by clicking on the cog icon.
Once your in, check your session is **Ubuntu** not **Ubuntu 2d** with
```
echo $DESKTOP_SESSION
```

---

### Post by qwertyjjj on 2012-02-22
> **stinkeye said:**
> When your at the logon screen make sure you choose Ubuntu as the session
by clicking on the cog icon.
Once your in, check your session is **Ubuntu** not **Ubuntu 2d** with
```
echo $DESKTOP_SESSION
```

Yep, started as ubuntu, logged in. When I click restart it just logs me out.
When I do subo reboot and log in again, unity is gone

---

### Post by stinkeye on 2012-02-22
How did you autostart xbmc?
Have you changed any other settings?
Did you do anything to do with saving sessions or editing sessions?

---

### Post by qwertyjjj on 2012-02-22
> **stinkeye said:**
> How did you autostart xbmc?
Have you changed any other settings?
Did you do anything to do with saving sessions?

Just on the system settings, there is an autostart option and you can add what you want. I took it off recently so it doesn't autostart anymore.
Didn't save any sessions I don't think.

---

### Post by stinkeye on 2012-02-22
Well sorry your problem is getting out of my league.
Only other things I suggest is run the unity test
```
/usr/lib/nux/unity_support_test -p
```

eg
```
glen@Oneiric:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

and check your GFX driver is activated in Additional Drivers.
How did you install xbmc?

---

### Post by qwertyjjj on 2012-02-22
> **stinkeye said:**
> Well sorry your problem is getting out of my league.
Only other things I suggest is run the unity test
```
/usr/lib/nux/unity_support_test -p
```

eg
```
glen@Oneiric:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

and check your GFX driver is activated in Additional Drivers.
How did you install xbmc?

from the repos, it's the stable version of xbmc.
All reponses say yes in the above test.

I tried restarting, it just logged me out again.
FWIW, on the login screen, there is the option to shtdown. I select shutdown and nothing happens.

Oh, the other thing I changed was turned auto login to ON. However, it never auto logs in, I always have to put the password in.
I tried going to Users and turning it off but I cannot unlock it.
Doesn;t this all sound like a permissions issue?

---

### Post by qwertyjjj on 2012-02-22
I updated the driver and now my screen res is incorrect, it doesn't fill the whole screen?

---

### Post by stinkeye on 2012-02-22
You think it might be easier to backup and do a fresh install?

---

### Post by qwertyjjj on 2012-02-22
I think this is the bug:
[http://askubuntu.com/questions/90118/ubuntu-11-10-logs-off-when-clicking-shutdown](http://askubuntu.com/questions/90118/ubuntu-11-10-logs-off-when-clicking-shutdown)

---

