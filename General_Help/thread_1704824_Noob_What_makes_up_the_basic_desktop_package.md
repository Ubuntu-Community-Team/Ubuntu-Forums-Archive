---
title: "Noob: What makes up the basic desktop package?"
date: 2011-03-11
forum: General Help
---

### Post by DeltaWolf7 on 2011-03-11
Let me clear up my question a little.

If I install Ubuntu Server and lets say I want to add a desktop environment but don't want to use ubuntu-desktop, etc, what are the must haves to build the desktop?

Windows manager, mouse controller?

I am a total noob and want to learn what makes up the whole desktop system and then maybe create/build up a custom version for my needs.

Thank you,


Craig

---

### Post by lithopsian on 2011-03-11
Add X and all that comes with it, including video and input drivers.  Add Gnome and all that comes with it.  Add a windows manager like Metacity and all that comes with it.  Maybe add some themes if you don't like what the basic packages drag in.  Or you can just add X and not much more if you are hot stuff with scripting.

---

### Post by DeltaWolf7 on 2011-03-11
> **lithopsian said:**
> Add X and all that comes with it, including video and input drivers.  Add Gnome and all that comes with it.  Add a windows manager like Metacity and all that comes with it.  Maybe add some themes if you don't like what the basic packages drag in.  Or you can just add X and not much more if you are hot stuff with scripting.

Ok, starting to get the idea.

So, correct me if I am wrong...

X is a system that handles the video hardware, mouse, keyboard and other input/out put.

Window managers handle as they suggest the boxes (dialogs/windows) on screen.

So im guessing gnome, kde, etc are for styles? or are they for features?

Can you or someone give me the proper names for what make up a desktop system?

---

### Post by mssever on 2011-03-11
X provides the essential features for a graphical environment. 

Window managers provide window decorations (title bars, buttons, etc.) and specify rules for window behavior (resizing, focus, etc.).

Gnome, Xfce, and KDE are examples of desktop environments. A desktop environment packages many desktop items (window manager, panels, file managers, certain apps) into a convenient package. If you're looking for a barebones system, you can very easily skip a desktop environment. However, you almost always require a window manager, and there are many WMs that don't assume that they are paired with a desktop environment.

---

### Post by rowland on 2011-03-11
Watch out noob here:
Is it possible to change the desktop environment without reinstalling the whole OS again? And having 2 desktop environments at the same time, having the option to choose?

Compiz and beryl are extras for a desktop environment or is it X?

---

### Post by mssever on 2011-03-11
> **rowland said:**
> Watch out noob here:
Is it possible to change the desktop environment without reinstalling the whole OS again? And having 2 desktop environments at the same time, having the option to choose?
You can have as many desktop environments installed as you like. When you log in, there's an option to choose which one you want to use. No need to reinstall (actually, there are very few situations in Linux that really require a reinstall).

> Compiz and beryl are extras for a desktop environment or is it X?They are window managers.

---

### Post by matt_symes on 2011-03-11
Hi

> I am a total noob and want to learn what makes up the whole desktop system and then maybe create/build up a custom version for my needs.

Can i suggest you have a look at Arch Linux with a minimal install and build from there.

Configuration, package names, package manager etc can be different than Ubuntu but it will teach you about the subsystems required to build a working install (X, display manager, window manager, input output etc) The documentation is also pretty good.

Just a thought.

Kind regards

---

### Post by rowland on 2011-03-11
> **mssever said:**
> You can have as many desktop environments installed as you like. When you log in, there's an option to choose which one you want to use. No need to reinstall (actually, there are very few situations in Linux that really require a reinstall).

Any guide you know about how to install it?
And Compiz has to be installed for other window managers like KDE too? Or its enought to install compiz once?

Btw: you get notifications when you get a reply? Or how did you notice that i made a question?

---

### Post by Kep on 2011-03-11
First thing:

Don't use Ubuntu server if you just want to do so in order to customize your desktop environment. You will end up with a lot of packages you don't want and without many that you do want. You should instead use the Ubuntu alternate install CD or install a basic Debian system and build up from the command line that way. I kind of feel that Debian is the way to go if you don't want to take Ubuntu's default environment, but, each to his/her own.

Right. Now you need:

xorg: base of practically any graphical environment on linux

A login manager: I recommend slim. Or you can just run "startx"
A window manager: required. Examples include compiz, xfwm, kwm, openbox, fluxbox.

The window manager handles the windows. Many wms do other things too: fluxbox gives you a panel and menu, for example.

You probably want a file manager (nautilus/thunar are good choices).

Depending on above choices, you may need an application to draw a desktop background. Try feh.

You may need/want an application to draw icons onto the desktop. Don't know much about that.

You may need/want an application to add panels and stuff.

Be warned that it's not hard to end up in a horrible mess if you don't know what you're doing with this sort of thing ;)

---

### Post by DeltaWolf7 on 2011-03-11
Thank you all for your info. I will have a look a Debian as a base start point. I want to learn as much as possible, I have been using Ubuntu (desktop) for a while now but never go down to the ins and outs.


> **Kep said:**
> First thing:
Be warned that it's not hard to end up in a horrible mess if you don't know what you're doing with this sort of thing ;)

I don't mind the mess, as long as their be learning.. hehe, I will be working in a virtual box so if I do go wrong, I will be back with my saved state and a stack of questions.

---

### Post by ssri on 2011-03-13
> **matt_symes said:**
> Can i suggest you have a look at Arch Linux with a minimal install and build from there.

Configuration, package names, package manager etc can be different than Ubuntu but it will teach you about the subsystems required to build a working install (X, display manager, window manager, input output etc) The documentation is also pretty good.

Arch's lack of package signing is a huge security hole that leaves it exposed.  And no, md5 verification of packages does not cut it when it comes to security.

---

