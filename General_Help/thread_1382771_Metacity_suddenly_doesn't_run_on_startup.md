---
title: "Metacity suddenly doesn't run on startup???"
date: 2010-01-16
forum: General Help
---

### Post by ngrieb on 2010-01-16
I logged in today (running Karmic 32bit) and suddenly metacity doesn't run on startup, which of course renders many screen and window effects useless. What happened there? I'm concerned with what's causing it to fail. Anyone else having this problem? (I recently installed Audacious and a few gstreamer plugins. Is this the cause? )
Thanks.

---

### Post by n0dix on 2010-01-16
Post the Xorg.log errors and the .xsession-erros. You have to provide some information so that we can help

---

### Post by luke_lukem on 2010-01-19
Hi everyone,

I have the same problem, but i don't know when it started.
Here yo have my log files, but there's no mention of metacity.

I got around this by creating a desktop shortcut to metacity,
so i click it when i log in.

I hope this helps

---

### Post by ngrieb on 2010-01-20
Seems like it can't read the config file in .config/metacity/. What's the normal thing to do in this case? (backup, delete/move, and see if the config file gets rewritten to a default config file?) 

luke_lukem did you recently install Audacious by chance? 

Right now I just have Metacity running on startup through the startup apps.

---

### Post by ionlywanttodownloadafile on 2010-03-01
Hi ngrieb!

Why did You mention audacious? 
Similiar experiences?

I know, Audacious is something other 
than audacity. But I installed audacity 
on Scientific Linux (a RedHat 5.4 clone) 
from dag.wiers rpm site - and 
gnome-session completely dissappeared!!

I had to reinstall gnome-session via yum.

What is happening there??

max

---

### Post by ngrieb on 2010-03-07
No clue, I also have Audacity but have had it for many months with no problem. I know that Audacious has its own skin set, and might have somehow made Metacity freak out...? I have just added Metacity to my start up programs to cover the problem for now.

---

### Post by flippo on 2010-03-07
Heres a fun one.  I have had a similar issue and boy, it is tough to figure out.  If you have a file gnome-wm.desktop in your ~/.local directory (you can figure this out with "find ~/.local -name 'gnome-wm.desktop'" and this file has the line Hidden=true gnome-session will fail to launch a wm on boot up.  The easiest fix is to just delete the gnome-wm.desktop file.

Is this your issue?

(as an FYI alacarte, the gnome menu editor, can create this file under certain circumstances when you edit your gnome menus)

---

### Post by haneya on 2010-03-12
Hi, I have similar problem, I edited the menus using gnome-editor if that helps, Xorg.log and .Xsession-error will be attached, Thanks.

Edit: I just removed these two files and every thing went back to normal (gnome-wm.desktop, genome-metacity.desktop)

Anas

---

### Post by iShurtugal on 2010-06-14
> **haneya said:**
> Hi, I have similar problem, I edited the menus using gnome-editor if that helps, Xorg.log and .Xsession-error will be attached, Thanks.

Edit: I just removed these two files and every thing went back to normal (gnome-wm.desktop, genome-metacity.desktop)

Anas

I deleted gnome-wm.desktop, and now it's working!  this WORKS!

---

