---
title: "X11-server / Bare Bones Gnome"
date: 2009-11-16
forum: General Help
---

### Post by oaxacamatt1 on 2009-11-16
Hi all,
I want to install a bare bones Ubuntu 9.10 from the server disk and 'overlay' (the right term?) a bare bones Gnome. I want to have a very minimal gnome-core install without all the 'extras'. 

Let me explain, I decided to start from the 9.10 server disk and build up from scratch.  I loaded the server, gnome-core, gdm network-manager, gnome-utils, synaptic and X11-server. 

When I loaded X11-server I noticed that a lot of cr-- loaded too.  Is there a way to load only the stuff I want??

---

### Post by Giblet5 on 2009-11-16
Of course there is, but you won't do it from Synaptic.

You didn't think this question through. Either that, or you think we're all clairvoyant and we somehow magically know what you want/don't want.

What is the point of this anyway? Disk space is $80 per terabyte. To put this in perspective: the disk space required to install every single Ubuntu application, tool, doo-dad, and hoom-ha, costs the same as a medium-sized cup of yesterday's nasty gas station coffee.

Why do you want a "minimal" something, then choose a bloated environment like gnome? That's like asking for a Ferrari GTO that gets 70MPG and won't go faster than 25MPH.

Start over: tell us what your goal is, then we'll help you achieve/exceed that goal.

---

### Post by oaxacamatt1 on 2009-11-16
Giblet,
thanks for the help, but no thanks, i dont need the atitude.  

Why I want to do this is for my own education and fun.  I dont need someone making it a hassle.

---

### Post by Giblet5 on 2009-11-16
Take a look at "lubuntu-desktop". It's supposed to be light-weight gnome.

Install it via ```
sudo apt-get install lubuntu-desktop
```

Then, log off and select Lubuntu from the login screen's sessions menu.

---

### Post by julianb on 2009-11-16
In other words:

If you are trying to do what LXDE is good at (being light on RAM, light on disk space while still easy to use) then use the LXDE-based "lubuntu-desktop" or a similar setup. (consider [Masonux]("http://sites.google.com/site/masonux/"))

If you are trying to do what GNOME is good at (maximizing Linux's easy-of-use and functionality, targeted at machines that have at least 512MB of ram) then use GNOME.

---

### Post by QLee on 2009-11-16
[QUOTE=oaxacamatt1]
I want to install a bare bones Ubuntu 9.10 from the server disk and 'overlay' (the right term?) a bare bones Gnome. I want to have a very minimal gnome-core install without all the 'extras'.[/QUOTE]

Well, the term you used, "overlay" is not the way I think of it but I think I understand your meaning.

Keep in mind that Gnome is a Desktop Environment, thus what *you* consider "extras" might not be what the developers or the rest of us consider extras. Most of them are probably part of the environment (and they are made to work together smoothly).

[QUOTE=oaxacamatt1]Let me explain, I decided to start from the 9.10 server disk and build up from scratch.  I loaded the server, gnome-core, gdm network-manager, gnome-utils, synaptic and X11-server.[/QUOTE] 

In another post in this thread you wrote that you are doing this to learn. You could do this from Synaptic, although you'd have to be familiar with what you want and how to avoid installing "recommends", I cauthion against trying to "force" something to install without "dependencies". Read very carefully ,and understand, what the package manager states it is going to do before you allow it.

[QUOTE=oaxacamatt1]When I loaded X11-server I noticed that a lot of cr-- loaded too.  Is there a way to load only the stuff I want??[/QUOTE]

Perhaps some of what you consider cr-- might be something necessary for the system to function. Since you don't mention what it is, no way for us to help with that.

I just happened onto this thread and I apologise that I'm leaving the forum now after posting so I can't offer further help. Don't worry, plenty of people here will give you answers without "attitude" but realise, the way you phrased your question does seem a bit strange since "bare bones Gnome" seems to conflict with using a "desktop environment", naturally, people think you mean you want a "bare bones system" and thus suggest lighter weight window managers.

If you don't already know, learn about "dependencies" and "recommends". Remove anything you think you don't want but have restore plan for the time you un-install something the system needs. I suggest a dual boot with one partition for your test system, that way you could boot to the other partition and have a working system when you need to fix the test partition. Good luck.

---

