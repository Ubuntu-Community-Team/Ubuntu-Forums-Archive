---
title: "Customization"
date: 2010-03-20
forum: General Help
---

### Post by bigseb on 2010-03-20
I'm currently running 9.10 and I'm wondering if it isn't possible to turn certain features on or off. For example the dock that appears at the bottom of the screen, I don't dig it but it isn't under System ---> Preferences ---> Startup applications.

Also when I connect/disconnect my modem, can I change the size of the notification window and how long it stays on the screen?

Another is how to stop everything I plug in appearing on the desktop. I prefer an uncluttered desktop and would like to open plug-in devices through Places.

Any ideas?

---

### Post by darolu on 2010-03-20
> **bigseb said:**
> I'm currently running 9.10 and I'm wondering if it isn't possible to turn certain features on or off. For example the dock that appears at the bottom of the screen, I don't dig it but it isn't under System ---> Preferences ---> Startup applications.

Also when I connect/disconnect my modem, can I change the size of the notification window and how long it stays on the screen?

Another is how to stop everything I plug in appearing on the desktop. I prefer an uncluttered desktop and would like to open plug-in devices through Places.

Any ideas?
Right click on the bottom panel and click on "delete this panel", if you want it back, right click on the top one and add it back (or on the left/right); you can also hide it.

I don't know how to modify the notification window size, but it's probably under gconf-editor.

You can keep your desktop clean by following this steps: Press ALT+F2, in the window that pops up type "gconf-editor" (no quotes) hit enter and in the new windows navigate to: Apps - Nautilus - Preferences, look for the "show desktop" option and disable it.

---

### Post by bigseb on 2010-03-20
> **darolu said:**
> Right click on the bottom panel and click on "delete this panel", if you want it back, right click on the top one and add it back (or on the left/right); you can also hide it.
But that would kill the entire bar, all I want is to close the dock.

---

### Post by RabbitWho on 2010-03-20
> **bigseb said:**
> But that would kill the entire bar, all I want is to close the dock.

Hang on, dock? Do you have a dock as well as a panel? 
Panel is what I call those two bars you get on the top and bottom by default and docks are the things like on the bottom of the page here:
[http://o106.com/files/mandriva-ala-mego-docky.jpeg](http://o106.com/files/mandriva-ala-mego-docky.jpeg)

So if it's your panel you can make it transparent or put it on auto hide, or right click and "remove" bits of it you don't like if it has extra things added. 

I should mention I am running 9.4 and haven't tried 9.10 so if this is obvious to everyone else that's why it's not obvious to me.

---

### Post by bigseb on 2010-03-20
> **RabbitWho said:**
> Hang on, dock? Do you have a dock as well as a panel? 
Panel is what I call those two bars you get on the top and bottom by default and docks are the things like on the bottom of the page here:
[http://o106.com/files/mandriva-ala-mego-docky.jpeg](http://o106.com/files/mandriva-ala-mego-docky.jpeg)

So if it's your panel you can make it transparent or put it on auto hide, or right click and "remove" bits of it you don't like if it has extra things added. 

I should mention I am running 9.4 and haven't tried 9.10 so if this is obvious to everyone else that's why it's not obvious to me.
There is a dock as well as a panel. Can't find any settings to switch it off

---

### Post by RabbitWho on 2010-03-20
> **bigseb said:**
> There is a dock as well as a panel. Can't find any settings to switch it off

Aha! cool okay. 

If you go to system > system monitor > Processes you'll see a list of things that are running, and you should be able to find the name of the dock. You can kill it there too but it will still start up again when you restart, my hope is that by finding the exact name of the dock you'll be able to find it in the computer and edit its settings or uninstall it or find documentation online about it that will help you.

---

### Post by stinkeye on 2010-03-20
If your talking about the Window List applet, click just to the left of the first tab 
and there should be an option to remove from panel.

---

### Post by bigseb on 2010-03-20
Re: dock

Found some stuff relating to what can only be the dock but no options on how to turn it off. Where is msconfig when you need it...

---

### Post by darolu on 2010-03-20
> **bigseb said:**
> There is a dock as well as a panel. Can't find any settings to switch it off

What Dock did you install? most of them are launched on start up, go to your start-up applications and delete it/disable it from the list.

---

### Post by phibxr on 2010-03-21
> **bigseb said:**
> I'm currently running 9.10 and I'm wondering if it isn't possible to turn certain features on or off. For example the dock that appears at the bottom of the screen, I don't dig it but it isn't under System ---> Preferences ---> Startup applications.

Also when I connect/disconnect my modem, can I change the size of the notification window and how long it stays on the screen?

Another is how to stop everything I plug in appearing on the desktop. I prefer an uncluttered desktop and would like to open plug-in devices through Places.

Any ideas?

Could that dock perhaps be Gnome-Do?

---

### Post by stinkeye on 2010-03-21
A screenshot would help.

---

### Post by bigseb on 2010-03-21
> **phibxr said:**
> Could that dock perhaps be Gnome-Do?
I think it may well be. I certainly didn't install one. Incidentally, it only appeared when I started the visual effects.

---

