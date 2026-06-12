---
title: "Can I easily switch to &quot;server&quot; mode?"
date: 2006-04-03
forum: General Help
---

### Post by engineering.concepts on 2006-04-03
I have been playing with Ubuntu for the last month and I think I have it set up almost exactly as I would like, but it is a little on the slow side. I have checked with the forums on how to speed up the HD etc, but I would like to try to change to server mode. All of the posts that I have read tell me how to do it from a fresh install - I would not want to do that because I would lose all of my programs/settings and icons(or would I ?) - can I easily make this change from the regular install of Ubuntu 5.10? A command like ---- sudo servermode would be great :)  but I doubt it.
Any idea how much faster I could expect my machine to run with ubuntu server? (50% or more would be great - I hate to say this but a 30% improvement would bring me back to WinXP territory.) 
I would rather keep Ubuntu then give Bill satisfaction.
Thanks for your help!

---

### Post by stuporglue on 2006-04-03
Server mode has only a command line interface. You know that right? 

You can get rid of a lot of stuff by doing "sudo apt-get remove xserver-xorg gnome*"

I would suggest that you instead install Xubuntu. "sudo apt-get install xubuntu-desktop". 

Once it's installed, log out, then in the options menu on the log-in screen, select "XFCE session". XFCE is a lot lighter than Gnome (the standard Ubuntu desktop). I've used XFCE on ~300 Mhz desktops and it works great. 

Note: The Xubuntu desktop in Dapper is a LOT better than the one in Breezy. Dapper won't be officially released till June or so, but it'll be worth the wait. I'm using the devel version right now and it's really good.

---

### Post by engineering.concepts on 2006-04-04
Thanks for the info and command line information. 
Before I type "sudo apt-get remove xserver-xorg gnome*" I would like to know what I will lose and what will be different (basic overview). I would assume that if I don't like it I can just type in 
"sudo apt-get install xserver-xorg gnome*"
and everything will be back to normal?

I will play with this and just wait for the Dapper release I guess, - should the dapper release be any faster on a 900mhz system?
Thanks for your help

---

### Post by Toxicity999 on 2006-04-04
That was kind of just a vague suggestion... basically in doing that you remove anything GNOME related along with the graphical display ability in essence this would be ubuntu server... but in REALITY who wants just a command line interface for their home tasks these days? Take the secondary suggestion and install Xubuntu, then if you like it worry about dumping gnome. (if your last resort is reinstallation you really have nothing to lose anyway...)

---

### Post by stuporglue on 2006-04-04
> Before I type "sudo apt-get remove xserver-xorg gnome*" I would like to know what I will lose and what will be different (basic overview). 

Since giving those two items as things to be removed pulls in other items to be removed, Apt will ask you if you want to continue before it does it. When it asks you, it will give you a list of everything that will be lost. 

Essentially though, what you will lose is anything that involves graphics. Server mode is command line only. No GUI, no graphics. Press Ctrl+Alt+F1 to see what it will look like. 

> I would assume that if I don't like it I can just type in
"sudo apt-get install xserver-xorg gnome*"
and everything will be back to normal?

Your best bet would actually be to just do "sudo apt-get install ubuntu-desktop". The gnome* will actually try to remove some things that aren't installed. Installing ubuntu-desktop will bring it back to the initial post-install state. 

> I will play with this and just wait for the Dapper release I guess, - should the dapper release be any faster on a 900mhz system?

Some things have been optimized I believe, but I don't have any numbers for it. 

Unless you're sure you want a command-line-only interface, I'll reiterate my recomendation of trying out Xubuntu.

---

### Post by az on 2006-04-04
[QUOTE=engineering.concepts]I have been playing with Ubuntu for the last month and I think I have it set up almost exactly as I would like, but it is a little on the slow side. I have checked with the forums on how to speed up the HD etc, but I would like to try to change to server mode. All of the posts that I have read tell me how to do it from a fresh install - ![/QUOTE]

"server mode" is wrong.

What that is, is an option to boot the installer and not install the default desktop.  That saves on disk space for low-end machines.  It is also useful if you want to run ubuntu as a server, in which case you do not want a whole lot of software running on that bos - hence the name of the boot option.


If you are not short on disk space, you will have exactly the same effect on performance by installing xubuntu-desktop on your current system.  You will be running xubuntu in the same way, it's just that your dri ve will be fuller - which does not impact performance unless it is more than 95 percent full.

So, install xubuntu-desktop, log out and the change the session so that when you log back in, you are in the xfce session.  You can always log out and change it back.

Install icewm and menu if xf ce is not fast enough for you.  Same thing - switch your session to icewm to try it out...


You probably don't have a lot of ram, if you find a 900Mhz box fast.

---

### Post by engineering.concepts on 2006-04-04
Thanks for your help AZZ / Stuporglue / Tonicity999 - I will give your suggestiong a try - I am glad that I can easily switch back if I do not like the gui - I am just a bit confused by AZZ saying that "You probably don't have a lot of ram, if you find a 900Mhz box fast."
Is 384 megs of ram not enough for Ubunut? Should I have at least 512? What type of speed increase would i see?

---

### Post by az on 2006-04-04
[QUOTE=engineering.concepts] I am just a bit confused by AZZ saying that "You probably don't have a lot of ram, if you find a 900Mhz box fast."
Is 384 megs of ram not enough for Ubunut? Should I have at least 512? What type of speed increase would i see?[/QUOTE]
Sorry, I didn't see that.  You are fine with more than 128 megs.

---

