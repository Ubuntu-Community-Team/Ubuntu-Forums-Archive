---
title: "Accidentally screwed up the desktop"
date: 2011-04-30
forum: General Help
---

### Post by ticktoast on 2011-04-30
So.. yikes.
As the title says, I've basically gone and messed up my entire desktop. The curious (idiotic) me was experimenting with the desktop, and went and somehow deleted all the panels. After 3 days of frustration, I've been unable to recover any form of menu or panel.

So far, I've tried restoring the defaults from the terminal. Unfortunately, I can't open a terminal window. I can run it using Ctrl+Alt+F2, but it refuses to open any windows or run any programs. Most commands give me some form of 'cannot open display.'

It's been a big mess. I can't minimize windows without losing them so my workspace is a mess, I can't run nautilus as root so I can't access Synaptic, and the list basically goes on and on. Any help at all would be greatly appreciated!

---

### Post by s3a on 2011-04-30
Does ctrl+alt+f1 bring you to a terminal? Do sudo apt-get install ubuntu-desktop. If more issues arise, just tell us. Also, in the future, use a home partition that way if you accidentally screw things up again, all your files will be there and in the same place too with their configuration settings preserved.

---

### Post by ticktoast on 2011-04-30
The terminal opens, yes..
The only problem is that I don't run Ubuntu.. I'm using Ubuntu Studio, and I'm really not fond of the desktop for Ubuntu. Especially with Natty. The Unity stuff just goes right over my head, and I'd really prefer to keep it the way I had before...

When I try to install the Ubuntu Studio desktop, though, it says it is already installed, so there's not much I've been able to do...

---

### Post by s3a on 2011-04-30
Why don't you install everything that doesn't work? Example: sudo apt-get install nautilus. If you don't want Unity and installing ubuntu-desktop brings in Unity, can't you just remove it? The idea is that it pulls in everything else that you're currently missing.

Something like:

sudo apt-get install ubuntu-desktop;sudo apt-get remove --purge unity

I'm pretty sure those are the commands but I don't use Ubuntu as my primary OS so I'm not 100% sure.

---

### Post by dylbud on 2011-04-30
You can use Alt + F1 to bring up the main menu. At least you can open programs that way.

Also, Ctrl + Alt + T will open a terminal window but you stay on your desktop.

Maybe you could try bringing up the main menu with Alt + F1, and then right-click on an application and try to "add to panel." Maybe that will force a panel to appear.

I tried to experiment with this, but in my case it won't let me delete the last remaining panel, and the help documents explicitly state that you cannot delete the last panel and that there must always be at least one. Makes me wonder if somehow your panels are hidden.

---

### Post by ticktoast on 2011-04-30
Hmm... The dependencies aren't met for installing ubuntu-desktop, so that's not really working out...

> You can use Alt + F1 to bring up the main menu. At least you can open programs that way.

Unfortunately, it doesn't open the menu. No keyboard shortcuts I've tried have been able to open it. I haven't been able to access it at all..

---

