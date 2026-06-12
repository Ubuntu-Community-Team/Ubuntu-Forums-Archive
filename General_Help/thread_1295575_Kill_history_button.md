---
title: "Kill history button?"
date: 2009-10-19
forum: General Help
---

### Post by Randypan on 2009-10-19
Hello

I'm used to working with bookmarks and not with history menus in my browser and my filesystem. Allthough history (recent documents etc.) may help in a single session, I hate leaving traces of my previous activity on the next boot, so every time I'm about to shut down, I have to manually erase browser history, gnome menu recent documents and nautilus directory history. I have to admit this behaviour is a bit obsessive, for example I may erase everything after visiting a single website and just my home folder, but that's what I'm used to.
So I'm asking, is there a way to unify all these commands under a single launcher on my desktop? Something like a 'Kill History" button that would run the commands to erase my browser, gnome and nautilus history? 

Note that I don't want to disable history, since it helps on a single job but when I don't need it anymore I want it erased.

---

### Post by Tamlynmac on 2009-10-19
One simple suggestion is to use the Private Data settings to erase your history when closing Firefox.

firefox/edit/preferences/Privacy/Always clear my private data when I close Firefox/settings

You can check mark the individual setting you want cleared when Firefox closes. You can also add the "Toolbar Buttons" (A Firefox ADD ON) which contains a lock button (looks like a padlock) used to clear private data and place it in your Toolbar for clearing data while Firefox remains open and running.


Hope this Helps...

---

### Post by mordecai83 on 2009-10-19
Hello,

I might be able to help you a bit.

For gnome recent documents there is no option to disable it, but you can get around it by removing the history file and making it a directory, like so:

```
rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel
```

this will disable and grey out the recently used documents, you might have to restart, i don't remember.

For your browser, if you use firefox you can choose custom privacy settings and enable the "clear history when firefox closes" option and even fiddle around with the settings to choose what you want firefox to remove when it closes.

I hope this will help you a bit, i don't have anything for nautilus tho. but maybe someone else does.

With kind regards,
Mordecai

---

### Post by Randypan on 2009-10-19
These suggestions wouldn't save me the trouble of clearing firefox, gnome and nautilus individualy. What I'm looking for is a way of unifying these commands under a single button on my desktop or taskbar. If Firefox isn't possible, then just Gnome and Nautilus. I don't know much... Isn't there a CLI equivallent of every command executed via the graphical interface, like clearing the history archive in my case? Couldn't then a custom application launcher run these commands?

---

### Post by K.Mandla on 2009-10-19
> **Randypan said:**
> These suggestions wouldn't save me the trouble of clearing firefox, gnome and nautilus individualy. What I'm looking for is a way of unifying these commands under a single button on my desktop or taskbar. If Firefox isn't possible, then just Gnome and Nautilus. I don't know much... Isn't there a CLI equivallent of every command executed via the graphical interface, like clearing the history archive in my case? Couldn't then a custom application launcher run these commands?
I usually clear histories manually when I launch a program, using an alias that calls a script that cleans up after them. 

For example ... [http://kmandla.wordpress.com/2009/07/24/cleaning-up-is-hard-to-do/](http://kmandla.wordpress.com/2009/07/24/cleaning-up-is-hard-to-do/)

---

### Post by Randypan on 2009-10-19
Then should I include a command for deleting the recently-used.xbel file and creating a new one, to clear recent documents? What about nautilus history?

---

### Post by mordecai83 on 2009-10-20
Hello again,

> These suggestions wouldn't save me the trouble of clearing firefox, gnome and nautilus individualy

Ehm...., yes they would. By applying the recently-used.xbel trick there is no file to write too so gnome will not remember the recent documents you opened. So there is no need to manually clear them. Same goes for firefox, if you enable clear history on exit firefox does it for you every time you close it. So i really don't see why this wouldn't help you, unless... you're extremely paranoid and don't trust the computer to do it for you and you need to do it manually.

With kind regards,
Mordecai

---

### Post by dj-toonz on 2009-10-20
Or you could use a program like bleachBit to do everything in one go for you (like ccleaner under windows). I've got everything ticked for Firefox & under System - Recent Document List, Temp files & trash

---

### Post by Randypan on 2009-10-20
Thanks! BleachBit suits me just fine. I didn't want to disable history, I just wanted to control all system histories with one application and Bleachbit does the job perfectly. In the perfect world inside my head I could be able to do that with a single click, but two clicks is not that bad either... Thanks again

---

### Post by Randypan on 2009-10-20
...It didn't work out well in the end. Bleach is quite capable an application but I enqountered a problem. The option to erase nautilus history works a bit by brute force, completely emptying the ~/.nautilus/metafiles directory. Apart from the history .xbel files , thumbnail settings files are also stored there. And when there are over 500 music albums in your hard drive, displayed in large scale icons, with each one's album art copiously selected and displayed and you lose all that from one moment to another... well that just discouraged me from using it any further, after trying hard to fool Bleach into not erasing everything in there of course ( I tried changing permissions to 'root' for 'metafiles'- but then Bleach couldn't erase anything, did the same thing just for the 'x-nautilus-desktop file' but that way it still got deleted)

I then turned back to trying my launcher idea. I set up a 'launch in terminal' button with the following commands:

rm recently-used.xbel & rm ~/.nautilus/metafiles/"that-xbel-file-with-the-really-long-name-I-found-in-that-directory''

At first it seemed to work. The files were gone. But the menu entriy for the recently used just wouldn't go away -not even after reboot. I tried including:

 rm recently-used.xbel && touch recently-used.xbel

and a couple more things but they didn't work either.
I think I'll give up now. At least I learned a couple of things in the process. -Should I mark the thread 'solved'?

---

