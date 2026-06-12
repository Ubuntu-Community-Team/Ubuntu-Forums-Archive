---
title: "2 Questions"
date: 2006-04-13
forum: General Help
---

### Post by user1397 on 2006-04-13
Q#1) Howcome if there are minimized windows on desktop #1, (I have ubuntu installed with the kubuntu packages) they are still there in desktops #2,3,4?
This doesn't happen in ubuntu!

Q#2) How come when trying to play a song in amaroK or rhythmbox in kubuntu, it says "Gstreamer error..."?

---

### Post by Sef on 2006-04-13
> Q#2) How come when trying to play a song in amaroK or rhythmbox in kubuntu, it says "Gstreamer error..."?

Just type in the gstreamer commands and see if it helps.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by user1397 on 2006-04-13
[quote=Sef]Just type in the gstreamer commands and see if it helps.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")[/quote]
No, all of them are already installed. :(

---

### Post by user1397 on 2006-04-13
Oh and one more question: What is the kubuntu equivalent of the "startup programs" tab in sessions?

---

### Post by Sef on 2006-04-13
> No, all of them are already installed. 

1) Are you sure you didn't miss one?

2) Maybe one got corrupted.

---

### Post by user1397 on 2006-04-13
I'm sure Igot all of them but I don't know about corruptions..........

---

### Post by Hanj on 2006-04-14
> Q#1) Howcome if there are minimized windows on desktop #1, (I have ubuntu installed with the kubuntu packages) they are still there in desktops #2,3,4?
This doesn't happen in ubuntu!You need to click the taskbar menu, select "Configure taskbar" and deselect "Show windows from all desktops".

---

### Post by uteck on 2006-04-14
You esiest way to autostart a program is to copy the application launcher from the kmenu,(or make a new launcher if yo know how) to ~/.kde/Autostart

---

### Post by Neo Ex on 2006-04-14
[QUOTE=erik1397][...]
Q#2) How come when trying to play a song in amaroK or rhythmbox in kubuntu, it says "Gstreamer error..."?[/QUOTE]
Be sure to have installed all GStreamer plugins:
```
sudo apt-get install gstreamer0.8-plugins
```
Then, run
```
gst-register-0.8
```
If amaroK doesn't play songs yet, install the amarok-xine package, and go in amaroK configurations and select it as the engine instead of the aRts one. I did so and it works.

---

### Post by user1397 on 2006-04-14
Thanks guys for all the replies.

---

### Post by RS3York on 2006-04-15
I'm not sure about your gstreamer problem.  Ver 0.10 is good on the soon to arrive Dapper, so you're problem with it should be short lived.  

The easiest way to autostart apps in KDE is simply to leave them open when you log out/shutdown/restart.  KDE will "restore your session" there by also starting any apps you left open the last time KDE shutdown.  There's also an option to manually save a session, so you can set up the ideal "starting environment" save that session, and then those apps will start everytime you log into KDE.

---

### Post by user1397 on 2006-04-15
[quote=RS3York]I'm not sure about your gstreamer problem.  Ver 0.10 is good on the soon to arrive Dapper, so you're problem with it should be short lived.  

The easiest way to autostart apps in KDE is simply to leave them open when you log out/shutdown/restart.  KDE will "restore your session" there by also starting any apps you left open the last time KDE shutdown.  There's also an option to manually save a session, so you can set up the ideal "starting environment" save that session, and then those apps will start everytime you log into KDE.[/quote]
I see... thanks

---

