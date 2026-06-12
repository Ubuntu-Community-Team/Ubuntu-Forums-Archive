---
title: "3 Problems: boot, hibernation, and notifications :)"
date: 2009-12-25
forum: General Help
---

### Post by ondiron on 2009-12-25
Hello :)

So I have three problems in order from most important to least important:

1. Booting.
Sometimes, my laptop will boot just fine and load into GRUB. (I only have Ubuntu installed)

However, sometimes it will just hang on the screen that has "press F2 to access options, F12 to change boot order". I found out that usually if I turn it off and on a couple times it will boot.


2. Hibernation (?)

Okay, with a previous version of Ubuntu it didn't do this but now: If I plug in my power cord (or unplug) my computer goes to the lock screen. Not that bad, but after I unlock it, the laptop hibernates. This is annoying, especially if I plug in the cord while downloading something big because it disconnects from my network.


3. Notifications.

How do I access settings for the notification boxes? (you know, the semi-transparent box that shows volume, "connected to network", etc.)

I only want to change how long they display for.





Thanks much for the help!

-ondiron

---

### Post by tom.swartz07 on 2009-12-25
> **ondiron said:**
> Hello :)

So I have three problems in order from most important to least important:

1. Booting.
Sometimes, my laptop will boot just fine and load into GRUB. (I only have Ubuntu installed)

However, sometimes it will just hang on the screen that has "press F2 to access options, F12 to change boot order". I found out that usually if I turn it off and on a couple times it will boot.


2. Hibernation (?)

Okay, with a previous version of Ubuntu it didn't do this but now: If I plug in my power cord (or unplug) my computer goes to the lock screen. Not that bad, but after I unlock it, the laptop hibernates. This is annoying, especially if I plug in the cord while downloading something big because it disconnects from my network.


3. Notifications.

How do I access settings for the notification boxes? (you know, the semi-transparent box that shows volume, "connected to network", etc.)

I only want to change how long they display for.





Thanks much for the help!

-ondiron

Hi and Welcome! First post! 

Lets see how I could help;

1.) Not too sure of whats going on here, perhaps you might just accidentally hit a key on your keyboard as it boots and it interrupts the grub menu.

2.) Look in System>preferences>power options and see if you have an option checked there to tell it to hibernate or sleep when its on battery/AC

3.) There is a way using gconf-editor, but I cant seem to find it right now. it involves editing one or two simple lines. Perhaps try ubuntu-tweak. That program might have options to configure it easily.

---

