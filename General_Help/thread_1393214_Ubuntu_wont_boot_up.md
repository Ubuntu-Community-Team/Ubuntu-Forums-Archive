---
title: "Ubuntu wont boot up"
date: 2010-01-29
forum: General Help
---

### Post by Sodlig on 2010-01-29
So, I was trying to install my Intel g card driver onto the ubuntu which I got on a seperate disk from my XP (Dual boot).
I shut the machine off after the drivers were installed (Guess they got installed, could be they didn't).

Somehow it wont boot up now, it's just showing a black screen.
I was browsing round the forum boards here and came across another thread of a guy having kind of the same problem, though the thread is kind of out dated (2007).
Anyhow, so it was said that he inserted and booted from his Live CD and then copied the xorg.conf file from the Live CD to the machine itself.

So my question is, will this work and how will it work?
I heard about a console/terminal showing up and I'm not fully aware of every command being made there, so I could need some help of how-to copy these files there and how to get onto the console.

Thanks a lot in advance,
Sodlig.

---

### Post by tom4everitt on 2010-01-29
Short answer, yes it might work. It will replace your current settings with the standard settings. Opening a terminal on a live cd is as easy as: 

1. booting from the live cd
2. go to applications->accessories->terminal (in the top left menu).



EDIT: If you want help with specific commands you would have to post a link or the commands themself.

---

### Post by Sodlig on 2010-01-29
Well, I'm wondering which command I should use to overwrite my old settings to the default settings from the Live CD.

When I tried booting it up with CD drive as first boot option, I just gotten into the installation progress.
I'm a bit worried since I don't feel like overwriting my WinXP.

---

### Post by sandkernel on 2010-01-29
Sounds like it actually boots up but is having difficulty loading X-Windows. I'd boot the machine then do <ctrl><alt><F2> all at once. See if you get a log in screen. I bet you do. Once you do, log in with your id and password and then sudo to root - > sudo su - . Next pop your cd in and copy the xorg.conf over or edit the file directly to make the changes you think necessary.

---

### Post by Sodlig on 2010-01-29
I'm afraid Ctrl + Alt + F2 doesn't have any effect.

---

### Post by tom4everitt on 2010-02-01
Don't worry about going through the installation process, it will not erase your windows without asking you first. 

At some point in the installation you will be asked whether to install it beside windows, or on the entire hard drive, or configure it manually. Manual does give most control of course.

---

### Post by Monotoko on 2010-02-01
I would try and boot into single user mode (Recovery Mode from your GRUB menu) then choose "Xfix" from the menu that comes up

---

### Post by Jotham on 2010-02-01
It doesn't sound like you're using the Live CD, or you might be choosing the wrong option. Choose "Try Ubuntu without any change to your computer".

You'll probably have to mount your hard drive once you boot to the live cd.

---

