---
title: "I Loooove Ubuntu"
date: 2009-11-30
forum: General Help
---

### Post by Cordobah on 2009-11-30
Dear Anyone
                  Hello, My name for now is Cordobah and I have fallen in Love with Linux for the First time truly. I have tryed Linux several times in the past 10 years or so but I just never seemed to get it to work properly or I would have driver problems mostly, but with Ubuntu I Finnialy feel I have found an OS that I truly love. I have had pretty much no problems up untel now and I just installed it about 3 days ago. Softwares all installed with ease, Drivers for my Devices are OK. I just have a Small Problem with the (Cairo Dock) ! I would love to be able to Configure it to Start with the System, It also sometimes shows a Black box around the Dock blocking out the Wallpaper around the Dock.  Mostly I would love it if anyone out there with Linux Experance wouldn't mind spending some time with me to learn the basics that I Must know about Ubuntu or just some tips.. I think learning the Dir* and how it is lays out, how to install Programs and Drivers Manually.... also some of the Basic System Functions that I need to learn like System maintenance and so forth...
             
                                 Thank you for you time and Peace

---

### Post by Nekativ on 2009-11-30
I do not know much about your particular problem however, anything you want to have start with when Linux starts can be done by editing the 'upstart' file which is Ubuntu's variant of 'inittab'.

---

### Post by u.b.u.n.t.u on 2009-11-30
Cordobah, cool that you are so enthusiastic about Ubuntu.

You mentioned you wished a program to start by default. There may be two options. Within the program look for either preferences or options where such may be activated. Also there is a GUI for which programs start up by default.

I don't have Ubuntu running at the moment so I can't check the location.

It looks something like this:
[http://www.johannes-eva.net/images/2009%2004%20-%20Ubuntu%20Jaunty%20Jackalope%20Useful%20Guide/Ubuntu%209.04%20Jaunty%20Jackalope%20-%20Gnome%20-%20Startup%20Applications%20Preferences.png](http://www.johannes-eva.net/images/2009%2004%20-%20Ubuntu%20Jaunty%20Jackalope%20Useful%20Guide/Ubuntu%209.04%20Jaunty%20Jackalope%20-%20Gnome%20-%20Startup%20Applications%20Preferences.png)

With regards to learning about Ubuntu, there are many approaches from formal study to casual daily usage.

...

Edit Update:

Okay, running Ubuntu.

You may want to check out:

System\Preferences\Startup Applications

This Ubuntu community board is an excellent place to learn and share ideas.

---

### Post by lidex on 2009-11-30
First, what graphics platform are you on? nVidia, ATI/AMD, Intel? As u.b.u.n.t.u states, go to system>preferences>startup applications. Click the "Add" button. In the resulting dialog (for nvidia) enter ```
GLX-Dock (Cairo-Dock with OpenGL)
``` in name field. Enter ```
cairo-dock -o
``` in command field. Click the "Save" button, then "Close". For ATI follow same procedure except name= ```
Cairo-Dock (no OpenGL)
``` and command= ```
cairo-dock -c
```

---

### Post by lidex on 2009-11-30
To find video info quickly enter this command in a terminal:
```
sudo lshw -C display
```
You can find a terminal in accessories menu.

---

### Post by zaphod777 on 2009-11-30
under system -> preferences -> startup applications you can make it auto start

---

