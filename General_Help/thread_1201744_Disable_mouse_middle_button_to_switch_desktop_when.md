---
title: "Disable mouse middle button to switch desktop when scrolled"
date: 2009-07-01
forum: General Help
---

### Post by UranUtan on 2009-07-01
Hi,

Using Ubuntu 9.04 x64. I often scroll the mouse middle button when reading web page. Quite often the mouse focus is not on Firefox and I ended up scrolling back and forth between multi desktop workspaces.

Is there a way to disable the mouse scroll to switch Gnome desktop workspace?

---

### Post by thermisius on 2009-07-01
spaghettti
[IMG]http://i711.photobucket.com/albums/ww111/thermisius/untitled.jpg[/IMG]

---

### Post by UranUtan on 2009-07-01
Sorry, I don't understand the answer. I was not asking about food. Are you sure you are in the right forum?

---

### Post by ronaldprettyman on 2009-07-01
Yes, the easiest way is just to disable multiple desktops if you don't use them. Right click on the desktop switcher and set both to one

I'm sure theirs a way to disable that feature and still have multiple desktops, but I'm not aware of it.

---

### Post by UranUtan on 2009-07-01
> **ronaldprettyman said:**
> Yes, the easiest way is just to disable multiple desktops if you don't use them. Right click on the desktop switcher and set both to one

I'm sure theirs a way to disable that feature and still have multiple desktops, but I'm not aware of it.

Sorry but this sound too extreme as a solution. I do want multiple desktops, there should be a way to disable the scrollwheel behaviour.

EDIT: found solution here, just need to formulate the right keywords to hit a positive search results: [http://ubuntuforums.org/showthread.php?t=601716](http://ubuntuforums.org/showthread.php?t=601716)

> Compiz Config Settings Manager: Viewport Switching: must be UNCHECKED

Strange that all this wording means disable mouse scroll wheel.

---

### Post by drs305 on 2009-07-01
For keyboard enthusiasts, you can retain keyboard workspace switching in compiz without disabling it completely. Disabling 'workspace switcher' in compiz's configuration settings manager will disable all workspace switching via keyboard combinations or mousewheel movement unless you directly click on the specific workspace in the panel.  

You can leave "Viewport Switcher" enabled and still use keyboard commands AND keep the mouse from changing workspaces.  

To enable keyboard switching, go to ccsm's (CompizConfig Settings Manager) Desktop, Viewport Switch. Enable it, then on the 'Go to specific viewport' set the key combinations you want. Notice the icons in this tab are keyboards.

To DISable the mouse actions, go to the next tab, Desktop-based Viewport Switching and DISable each (mouse) option.

Of course, if you want mouse switching but not keyboard switching, you can do the reverse.  ;-)

---

### Post by Netmonger on 2009-07-16
If you are talking about the desktop switching when using GLX, yes there is a real easy way to do this..

Install compizconfig.

Go to:  System -> Preferences -> 'CompizConfig Settings Manager'

Display the 'Viewport Switcher' under the 'Desktop' section.

You can still configure keyboard events to switch desktops from: 

System -> Preferences -> Keyboard Shortcuts

---

### Post by MadJester on 2009-07-16
Thank you, that was annoying...

---

### Post by bosvark on 2009-08-19
My mouse thanks you (I nearly smashed it out of frustration until I found this post).

---

### Post by mister_playboy on 2009-08-30
Thanks... this "feature" was incredibly irritating.  Another benefit is this seems to get rid of the hanging tooltip in the bottom right corner after each workspace switch... before, the tooltip wouldn't close unless moused over.

---

### Post by nrundy on 2010-12-26
Is there a way to disable this middle-mouse button behavior without installing Compiz-Config? A way from within Ubuntu (ie., without installing additional software)?

---

