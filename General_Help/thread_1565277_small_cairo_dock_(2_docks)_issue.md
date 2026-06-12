---
title: "small cairo dock (2 docks) issue"
date: 2010-08-31
forum: General Help
---

### Post by LifeEnemy on 2010-08-31
Hi all,

I currently have cairo dock set up to run two instances so I can us the main dock and get one to auto-hide without taking up space on the left side of my screen. I've been using the command "cairo-dock -o -d ~/.config/cairo-dock2/" to get the other dock going. I added that command to startup application but for some reason it won't appear when it starts. I have to put it into the terminal manually. How can I make it so both instance of cairo dock automatically run when I boot up?

Side issue: I've been wanting to use "keep below" instead of "auto-hide" for the side dock's behavior. When I move my cursor to the side of the screen it brings up the dock but it doesn't go back under my window when I'm done with it. Is this how it's supposed to happen?

Thanks for any help!

---

### Post by bobcollard on 2010-08-31
Right click on your second main dock and under Gmenu click open at startup.

After you have brought up the second dock you have to click away from it, like on the application you have open, to put it under again.

---

### Post by LifeEnemy on 2010-08-31
Thanks. I can't find the "open at startup" option, though. I have CD 2.1.3-9 if that matters.

EDIT: If you mean the GMenu applet, I don't have that on my side dock. Do I need it on there to make it work?

---

### Post by bobcollard on 2010-08-31
Sorry, gave you the wrong menu see attached.

---

### Post by LifeEnemy on 2010-09-01
seems like I don't have that option on my menu for some reason. I have everything else in your pic available.

I made the option appear if I deleted both docks from startup applications, but I can only add one dock and the option disappears from both. And no matter which dock I use, the command that gets put in startup apps is "cairo-dock -o" which I think would only launch the main dock on the bottom of the screen. Is there any way I can fix this, or some other way to get my dock to launch automatically?

Idea: is there a way to combine two terminal commands into one? Maybe if I could change the single cairo-dock startup command to one that would do both it would work. I don't know how to work in the terminal much, though.

---

### Post by bobcollard on 2010-09-01
> **LifeEnemy said:**
> seems like I don't have that option on my menu for some reason. I have everything else in your pic available.

I made the option appear if I deleted both docks from startup applications, but I can only add one dock and the option disappears from both. And no matter which dock I use, the command that gets put in startup apps is "cairo-dock -o" which I think would only launch the main dock on the bottom of the screen. Is there any way I can fix this, or some other way to get my dock to launch automatically?

Idea: is there a way to combine two terminal commands into one? Maybe if I could change the single cairo-dock startup command to one that would do both it would work. I don't know how to work in the terminal much, though.
If the bottom is cairo-dock 0 then the next would be cairo-dock 1  not (2).

---

### Post by fabounet on 2010-09-01
the latest version lets you have several docks with independant configurations, maybe it would be easier to use it :)
it's available here:
[http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en]("http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en")

---

### Post by LifeEnemy on 2010-09-03
I tried combing the commands for each dock with "&" but instead neither one of them launched. I think I'll try the newest beta version but I'll probably wait until I find the time to update to 10.04 first (running 9.04 right now).

---

### Post by LifeEnemy on 2010-09-08
> **bobcollard said:**
> Right click on your second main dock and under Gmenu click open at startup.

After you have brought up the second dock you have to click away from it, like on the application you have open, to put it under again.

I just tried setting my second dock to "keep below" and I realize the problem: even when I click away from the dock it stays. I can't get it to go away after moving my mouse to the side of the screen just once.

Maybe I'll just give the update a go and see if anything happens.

---

### Post by cpsully69 on 2010-09-30
I had a similar problem, I set Cairo to auto-start, from its menus, but I had also gone into gconf-editor (desktop->gnome->session->required components) and replaced gnome-panel with cairo-dock.

This started two docks.  Apparently, if you set it as your panel in gconf-editor, you DO NOT need to set Cairo to auto-start.

I then went to Preferences->Startup Applications, unchecked Cairo, logged out/in and I was down to one dock!

I hope this helps you out.

---

### Post by LifeEnemy on 2010-10-11
> **fabounet said:**
> the latest version lets you have several docks with independant configurations, maybe it would be easier to use it :)
it's available here:
[http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en]("http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en")

I finally got the new version, and I must say it is very nice! There's a lot of improvements on things I didn't even notice. It was very easy to set up another main dock, and I can even use "keep below" with it now. Thanks and Well done!

I have only one problem: I have the workspace switcher applet as a desklet, but it seems to only show 2 or my workspaces now (I have 3 in a row). I restarted but can't make it show the third one. I even tried "adding another workspace" on the right-click menu but it just made a 2x2 icon. It doesn't even show the third workspace on the window list via middle-click. Any suggestions?

---

### Post by LifeEnemy on 2010-10-19
bump. Still can't get the switcher to work right. The rest of the dock is still kickass, though.

---

### Post by LifeEnemy on 2010-10-20
bump

---

### Post by fabounet on 2010-10-22
was a bug, it's fixed on the trunk (development version).
it will reach the [weekly release]("http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en") soon :-)

---

### Post by LifeEnemy on 2010-10-22
Ah ok. I can wait for it, not a huge problem. Thanks.

How stable is th weekly release, usually? And what version number have you reached?

---

