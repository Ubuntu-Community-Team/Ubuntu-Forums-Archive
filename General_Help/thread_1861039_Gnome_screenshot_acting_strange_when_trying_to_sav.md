---
title: "Gnome screenshot acting strange when trying to save"
date: 2011-10-15
forum: General Help
---

### Post by scottbomb on 2011-10-15
I just upgraded to 11.10. I'm fairly new at Linux and I was checking out something I hadn't used before: gnome-screenshot (my version is 3.2.0-0Ubuntu1) and when I went to save the image it took, instead of opening a dialogue asking me where to save the photo, the screen turned purple and put what looks like a menu bar at the top (Has choices like File Edit View....) and I can't get it to close without logging out of my session and then logging back in (without saving session settings). Some of the options from this mysterious menu bar relate to connecting to a server. Very strange.

There are also two entries of "Screenshot" in my Applications Menu under Accessories. I can't seem to determine why. I opened Synaptic and searched screenshot and I see only one entry.

Any ideas?

[This post should probably be renamed "nautilus takes over screen and won't close". I guess that was the problem but how to really fix it so it doesn't happen again... I don't know]

---

### Post by scottbomb on 2011-10-15
Crap now I'm really in trouble. On the other computer, the upgrade broke some links I had in my home directory pointing to other folders on another drive. I know how to fix that but now it's also showing the purple background taking over the whole screen with that menubar at the top again. Some of my icons are gone and the others are rather distorted. It has "File Edit View Go Bookmarks Help". It's not Firefox. I click on File and some options are New Window, Create New Folder, Create New Document, Connect to Server. All Help has is Ubuntu Help which doesn't open anything. 

What is this thing and how do I get rid of it? I tried logging out and back in (with save session NOT checked) and I even rebooted but it won't go away.

---

### Post by scottbomb on 2011-10-15
OK, I found this:

ps -e | grep nautilus

it returned:

1903 ? 00:00:04 nautilus

I then typed: kill 1903

And my desktop is back to normal. What the hell was that all about? I guess nautilus is broken? Xubuntu has an application called File Manager that basically gives me the same functionality as Nautilus so I can use that. Is there a way to make it the default so Xubuntu doesn't try to open Nautilus (that won't close) for anything else?

---

### Post by scottbomb on 2011-10-15
Went into Settings Manager and Preferred Applications. Changed file manager from Nautilus to Thunar. I'll see how that works as a work-around until I can get to the root of this problem.

---

### Post by scottbomb on 2011-10-15
Well this will probably look a little silly as I ended up fixing the problem myself thanks to some more googleing. It appears that Nautilus likes to take over the entire desktop, obliviating all my xfce desktop settings. Since I like Xubuntu so much more than Gnome 3 and Unity, I figured I'd just do a fresh install of Xubuntu 11.10 and be done with it. That seems to have fixed these problems. I'm now on a quest to see if I can install my software like VLC, Dropbox, and some others on Xubuntu without having to monkey with Nautilus at all. Provided that works, I'll mark this thread as solved as it may be useful for anyone else who runs across this issue. Playing with multiple desktops on the same distro is akin to playing with fire in some ways but I suppose those who are more well-versed in Ubuntu will have those conflicts ironed out.

---

### Post by scottbomb on 2011-10-17
Well it looks like I will need Nautilus for Dropbox but at least now it's not set as the default file manager and thus destroying my desktop when another program tries to use it to save a file. I will likely use it only for Dropbox and for that purpose, I've created a desktop launcher that launches it with /usr/bin/nautilus --no-desktop and that at least seems to do the trick. 

As a side note, home networking/file sharing with Xubuntu was a nightmare until I discovered Gigolo, which seemlessly integrates network views with Thunar.

---

### Post by 23dornot23d on 2011-10-17
Check the link below ..... upgrade problems ..... 

I am trying to keep a list of them and marking the ones SOLVED so others can quickly find a
Solution ..... 

Hope this helps in some way

---

