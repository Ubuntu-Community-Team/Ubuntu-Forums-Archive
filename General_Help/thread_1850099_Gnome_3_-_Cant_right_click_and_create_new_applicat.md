---
title: "Gnome 3 - Cant right click and create new application shortcut"
date: 2011-09-25
forum: General Help
---

### Post by LinuxRocks on 2011-09-25
Hello All,

I am testing Ubuntu 11.10 and have fully updated the install and installed Gnome Shell.

I have also installed the gnome-tweak-tool and have enabled icons on my desktop.

What I am missing is the ability to create a new application shortcut on the desktop - or anywhere else for that matter.

Is there something I have to enable to be able to right click on the desktop and create an application shortcut?

I can right click and create a new text document, for example, but there is no option for an application shortcut.

So far, I have been creating the .desktop files manually, but that's getting old :-D.

Thanks!
Joe

---

### Post by LinuxRocks on 2011-09-25
Just checked Unity, and the same problem exists.

Any ideas?

---

### Post by hansdown on 2011-09-25
Hi LinuxRocks.

I don't think that feature is available in 11.10.

Someone may correct me, if that is not the case.

---

### Post by LinuxRocks on 2011-09-25
> **hansdown said:**
> Hi LinuxRocks.

I don't think that feature is available in 11.10.

Someone may correct me, if that is not the case.

Hi Handsdown, 

Thanks for replying!

Surely its a bug. How do the developers expect users to create launchers to start applications? 

If I have a package that I want to install, or one that I make or compile myself, how do we create launchers for these applications?

Should I create a bug report?

Thanks again!
Joe

---

### Post by hansdown on 2011-09-25
I don't think it is a bug; just a feature that is not yet implemented.

Again, I could be wrong.

---

### Post by .... on 2011-09-25
Try holding down Alt as you right click ;)
Real intuitive, huh?

---

### Post by LinuxRocks on 2011-09-26
> I don't think it is a bug; just a feature that is not yet implemented.

Again, I could be wrong.

Yeah, might just not be available yet...I have a work around, but its time consuming.

> 
Try holding down Alt as you right click 
Real intuitive, huh?


Hmm, I tried to press ALT and also tried the CTRL key (not at the same time) and neither worked for me.

Thanks for the replys!

Joe

---

### Post by .... on 2011-09-26
I thought you were talking about gnome-fallback (GNOME 3 with old-school panels), but I see you're referring to GNOME Shell. My apologies.

---

### Post by LinuxRocks on 2011-09-26
> **.... said:**
> I thought you were talking about gnome-fallback (GNOME 3 with old-school panels), but I see you're referring to GNOME Shell. My apologies.

Thanks for the info... It is actually a neat workaround though... I can use that to create my Desktop links and then log into Gnome Shell and they will be there.

Will be quicker than editing .desktop files :-D.

Thanks for the info!!!

Joe

---

### Post by ubutuist on 2011-09-27
You can't create an application shortcut in Gnome 3 by right-clicking on the desktop.

But there's a workaround.

Install Gnome 3 fallback session from Ubuntu software centre.

Log out and log back in Gnome classic.

Drag and drop application shortcuts on the desktop from the application menu.

Log out and log back in Gnome 3.

---

### Post by LinuxRocks on 2011-09-27
> **ubutuist said:**
> You can't create an application shortcut in Gnome 3 by right-clicking on the desktop.

But there's a workaround.

Install Gnome 3 fallback session from Ubuntu software centre.

Log out and log back in Gnome classic.

Drag and drop application shortcuts on the desktop from the application menu.

Log out and log back in Gnome 3.

Hi there :)

Thanks for the reply!

However, when I logged into "Fall Back" mode, I was not able to create a shortcut either. And, this seems to be an Ubuntu issue as my Fedora 15 install (Gnome 3/Shell) has no problems creating desktop application shortcuts - once you enable right click on the desktop.

So, it appears to be a bug. I will file a bug report on this.

Thanks so much for all your help!

Joe

---

### Post by Morbius1 on 2011-09-27
I had nothing better to do at the moment so I thought I'd see if something from lxde would let me create a desktop icon using Unity on Oneiric:

```
sudo apt-get install lxshortcut
```Then in a Terminal:
```
lxshortcut -o ~/Desktop/Firefox.desktop
```Filled in the boxes and changed the icon and I did get an icon on the desktop.

Didn't run. Got some incoherent error message about trusted source or something - guessed that it was because it wasn't marked as executable - made it so - and it works.

I would like to know if this also holds true for Gnome shell.

There's a moral to all this if a utility used in lxde has to be used to give you the same functionality ......... oh never mind ;)

---

