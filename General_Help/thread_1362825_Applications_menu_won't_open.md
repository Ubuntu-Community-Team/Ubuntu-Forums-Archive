---
title: "Applications menu won't open"
date: 2009-12-23
forum: General Help
---

### Post by Trogdole on 2009-12-23
Basically that's it. I have no idea what's wrong. I just uninstalled the KDE environment from my Ubuntu 9.04 installation, and now I can't open the Applications menu in my custom menu panel applet. In the main menu applet, the applications menu just doesn't appear. I haven't found anyone else with this problem, so I have no idea how to fix it. Any ideas?

Edit: Okay, so I just found a file in my .config folder called 'applications.menu', which is completely blank. Is this a problem?

---

### Post by oakgrove on 2009-12-23
That's weird.  As a very temporary work-around, you can open nautilus and go to /usr/share/applications and just open apps from there by clicking on them.

---

### Post by superstalker on 2010-01-08
I'm currently having the same problem... is there a way to fix it?
I can't even open the "Edit menu's"

And I really don't wanna reïnstall ubuntu... again... (well this time it's not actually my fault)

Edit:
I tried to open a game in Application -> Games.
As soon as I clicked it, my laptop was blinking the Numlocks and Capslock key. 
Couldn't move my mouse nor hear my music player, the whole thing just froze, only thing I could do was to reset my laptop.

When I restarted Ubuntu, the error occured.

Edit2:
The game continious to crash, when I opened it in terminal, it said the following: 
The VAD has been replaced by a hack pending a complete rewrite.

---

### Post by superstalker on 2010-01-09
Seriously... no one?

---

### Post by superstalker on 2010-01-09
Well... guess I have to reïnstall it again....

---

### Post by Natey on 2010-02-12
The exact thing happened to me. I am running a brand new copy of Ubuntu 9.10 on a Evo N800c compaq laptop. I am running absolutely nothing unusual and decided to install bzflag client, server, data and the main bzflag file from synaptic. 

As soon as I clicked it in the applications menu (applications, games, bzflag) it blinked on and off. Then i restarted, it gave me the bash prompt. I had to select the fix option from grub just to get it to run, then start x to get the x-server running again. 

Now, my application menu is clickable but nothing opens at all, and under System on the same menu, the Preferences and Administration menus are also missing. 

DO NOT INSTALL BZFLAG ON UBUNTU 9.10 Unless you see someone post a fix on here.

---

### Post by KWS48 on 2010-03-25
I am having this same problem.  I have a drop down menu for everything except applications.  I am trying to find the Ubuntu Software Center.  It does not seem to be anywhere yet it was listed as installed in Add/Remove.  I have since uninstalled Add/Remove using the terminal and tried to do the same with Ubuntu Software Center but I get an error saying " cannot find application".
Any suggestions.  I am using Ubuntu Studio 9.10  I do not want to have to reinstall as I have been using this since it first came out!  I am not new to the forums, but had to re-register because I could not reset my password.  ( different e'mail address than three years ago!

---

### Post by stoneage on 2010-03-25
Did you try System -> Preferences -> Main Menu? You can configure what is in the Applications drop down. If your .config/menus/applications.menu is also blank, mine looks like this:-
[http://www.pasteall.org/11942](http://www.pasteall.org/11942)

Obviously, you will have to change all the /home/username/ entries to your own username

---

### Post by lavinog on 2010-03-25
One work around is to create a new user. (no need to reinstall)
If you cant get the system menu do this:
alt-f2
users-admin

There are a couple of other workarounds, but this might be the quickest solution.

---

### Post by KWS48 on 2010-03-26
OK.  Tried that and got the drop down menu.  Ubuntu Software Center is not listed.

So now what do I do?  I no longer have Add/Remove nor Software Center.  If it isn't there, how can I install it?

When I tried to use the teriminal I got a message " no such application ".

---

### Post by macogw on 2010-03-26
What about deleting that file so it's regenerated?

---

### Post by lavinog on 2010-03-26
> **KWS48 said:**
> OK.  Tried that and got the drop down menu.  Ubuntu Software Center is not listed.

So now what do I do?  I no longer have Add/Remove nor Software Center.  If it isn't there, how can I install it?

When I tried to use the teriminal I got a message " no such application ".

```

sudo apt-get update

```
then
```

sudo apt-get install software-center

```

---

### Post by lavinog on 2010-03-26
btw How much free space do you have on your disk?

```

df -h

```

---

### Post by Thorney on 2010-05-22
> **macogw said:**
> What about deleting that file so it's regenerated?

Worked for me:
```
rm .config/menus/applications.menu
```

Error appears to have occurred that main partition runs out of space.

---

