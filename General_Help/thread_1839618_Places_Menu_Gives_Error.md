---
title: "Places Menu Gives Error"
date: 2011-09-06
forum: General Help
---

### Post by TurtleKing on 2011-09-06
I was simply installing some application on Ubuntu Classic 11.04 64 bit, when I notice the top panel disappeared for no reason. I decided to trying and recover it, but nothing would respond once it came back. I then tried deleting it to make another one, but it didn't let me. I went ahead and did some research on how to reinstall or relaunch the application, an got working again. However, everything was super default (looked older than what it came with) and the places menu gives errors for location.

I went ahead and customized the panel & restarted and now it's fine, but for some reason the places folder still brings up a pop-up errors:
```
Could not open location 'file:///home/bob
No application is registered as handling this file
```

I can open the home folder via the nautilus command. But I would love to have the places folder working again (kind of pointless to have there if it doesn't work). 

Any help would be appreciated.

Operating System: Ubuntu 11.04 64 bit
Version Problem Areas: Ubuntu Classic Places Menu + Ubuntu Unity File & Folders

---

### Post by TurtleKing on 2011-09-06
bump

---

### Post by TurtleKing on 2011-09-06
Changed the thread title to the actual error message.

Note: I tried the "open with" nautilus option. But it does not seem to affect the Places menu.

I hope someone can help me, so I don't have to re-install Ubuntu again this weekend.:cry:

---

### Post by Frogs Hair on 2011-09-06
Try opening the file browser and right click on the home folders and select open with other application . Select file browser from the list and check remember this application and try the places menu again .

---

### Post by TurtleKing on 2011-09-06
> **Frogs Hair said:**
> Try opening the file browser and right click on the home folders and select open with other application . Select file browser from the list and check remember this application and try the places menu again .

No check option for remember I am just going to reinstall.

---

### Post by Frogs Hair on 2011-09-06
You should see a window like the screen shot .

---

### Post by Krytarik on 2011-09-06
Frogs Hair, I'm wondering why those checkbox is still present at your system, since it has been removed for folders in April this year, even down to Lucid 10.04. Didn't upgrade your - currently running - system, or is this an old screenshot?

This is another way to set the association right:

Open the file "~/.local/share/applications/mimeapps.list" and make sure the entry for "inode/directory" is like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Greetings.

---

### Post by TurtleKing on 2011-09-10
Thanks. I am going to assume that would have fixed the problem, so I am marking the thread solved.

---

