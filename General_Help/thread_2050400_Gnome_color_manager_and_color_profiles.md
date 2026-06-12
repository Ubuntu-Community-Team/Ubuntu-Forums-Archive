---
title: "Gnome color manager and color profiles"
date: 2012-08-30
forum: General Help
---

### Post by cscj01 on 2012-08-30
Ubuntu 12.04 64-bit using Gnome Classic (No Effects)

I am a little confused about how Gnome Color Manager works.  I have color profiles in two different directories: /usr/share/color/icc and ~/.local/share/icc.  If I go to Applications>System Tools>System Settings>Color, I get a window showing my two scanners, my printer, and my computer.  If I Highlight either of the scanners and click Add Profile, I get a pop-up that has no profiles available.  One of my scanners is a Nikon Coolscan V ED, and I have a profile for it (in fact I have several) in ~/.local/share/icc.  So I have two questions.

1. Why do the profiles for the Nikon scanner not show in the pop-up window?

2. Why does my monitor not show in the list of devices?

Additionally, if I highlight the printer and click Add Profile, I get one profile in the pop-up window that is in /usr/share/color/icc.  Now, nothing in /usr/share/color/icc was added by me, and I don't know anything about the profile that is available for my printer.  However, that is not my concern at the moment.

If I go to ~/.local/share/icc and double-click any of the profiles, I get the following message> Color profile is already importedIf I go to /usr/share/color/icc and double-click any of the profiles, I get the following message: > Import color profile?So my final questions are how did the profiles I put in ~/.local/share/icc get imported (I didn't do it directly), and why are none of the profiles in /usr/share/color/icc imported?

---

### Post by cscj01 on 2012-09-02
bump

---

### Post by cscj01 on 2012-09-09
bump

---

### Post by cscj01 on 2012-09-13
Surely someone has some ideas here.  If not, I suppose I'll just close it.

---

### Post by cscj01 on 2012-09-15
Perhaps this is in the wrong forum.  Would the forum administrator move this to another forum if that is the case.  I really need an answer to this.

---

### Post by Milan Knizek on 2012-09-22
> **cscj01 said:**
> 
I am a little confused about how Gnome Color Manager works.  I have color profiles in two different directories: /usr/share/color/icc and ~/.local/share/icc.


The former one is for profiles, which have been installed system-wide. Usually via package manager (Krita, Gnome Color Manager, argyllcms and possibly others install some general profiles there) or you can copy the profiles there manually (requires root privileges, of course).

The latter one is for profiles installed by the user (e.g. via clicking on ICC file in Nautilus and installing via Profile installer, which is part of Gnome Color Manager).

> **cscj01 said:**
> 
If I go to Applications>System Tools>System Settings>Color, I get a window showing my two scanners, my printer, and my computer.  If I Highlight either of the scanners and click Add Profile, I get a pop-up that has no profiles available.  One of my scanners is a Nikon Coolscan V ED, and I have a profile for it (in fact I have several) in ~/.local/share/icc.  So I have two questions.

1. Why do the profiles for the Nikon scanner not show in the pop-up window?


I do not know, it could be a bug in Gnome Color Manager or the profile does not have the correct metadata, which are used by GCM to filter the profiles by device type.

> **cscj01 said:**
> 
2. Why does my monitor not show in the list of devices?


You have mentioned that "your computer" is listed among the available devices. That is weird, the computer is not a type of device, which could be color-managed.

Do you use proprietary drivers for your graphics card? (nVidia?) If so, GCM is not able to recognise the type and name of your display and therefore may show just a general device name for your display. Also, it may not be able to calibrate your screen with a colorimeter. You can work-around it by using open source drivers (nouveau).

> **cscj01 said:**
> 
Additionally, if I highlight the printer and click Add Profile, I get one profile in the pop-up window that is in /usr/share/color/icc.  Now, nothing in /usr/share/color/icc was added by me, and I don't know anything about the profile that is available for my printer.  However, that is not my concern at the moment.


If you want to add a profile for your printer, you need to create it first - this requires a special measuring device or you can use 3rd party services. Some inkjet paper vendors provide generic profiles for various printers, too. Simply download it and install via Nautilus. It should appear then in the list of profiles available for the printer.

> **cscj01 said:**
> 
If I go to ~/.local/share/icc and double-click any of the profiles, I get the following message: "Color profile is already imported."


If you install profiles via Nautilus by double-clicking, they are simply copied to ~/.local/share/icc. That is why it fails for the already installed profiles.

> **cscj01 said:**
> 
If I go to /usr/share/color/icc and double-click any of the profiles, I get the following message: "Import color profile?"


In this case, copying to ~/.local/share/icc is possible, hence no error message. Nevertheless, it does not make sense to install the profiles from /usr/share/color/icc directory to your home directory, since both locations are searched by Gnome Color Manager for a list of existing profiles.

> **cscj01 said:**
> 
So my final questions are how did the profiles I put in ~/.local/share/icc get imported (I didn't do it directly), and why are none of the profiles in /usr/share/color/icc imported?


Hopefuly you already know the answer to these last questions.

---

