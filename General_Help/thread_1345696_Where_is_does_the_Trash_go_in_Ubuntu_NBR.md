---
title: "Where is does the Trash go in Ubuntu NBR?"
date: 2009-12-04
forum: General Help
---

### Post by sebastianfaunes on 2009-12-04
Hi,

I'm a newcomer to ubuntu (from windows xp), and I'm happy with it so far. I have Ubuntu Netbook Remix on my Hasee 1.6ghz/2GB RAM 160GB HDD Netbook. 

Nevertheless, a big question has popped up, where does the trash go??? Whenever I delete something it just disappears, and I can't find any trash folder. (I want stuff to come back sometimes)

I tried to opt for displaying the trash bin on the desktop, following the instructions for Ubuntu 9.04, but all that did was not allow me open any folder at all. Luckily I was able to go back in, unselect that, and get things back to normal.

Any clues???

---

### Post by audiomick on 2009-12-04
Hi.
The normal Ubuntu has a Trash icon in the bar at the bottom of the screen on the right hand side.

---

### Post by sebastianfaunes on 2009-12-04
What's the file path of the contents of the trash can, at least to find it on the hard disk? Thanks for the last post audiomick

---

### Post by Jim_in_Germany on 2009-12-04
The path is:

/home/username/.local/share/Trash/

where username is your user name

P.S. In this folder you'll find 3 folders, "expunged" files" and "info". As you might expect, deleted files are in "Files"

---

### Post by sebastianfaunes on 2009-12-04
Thanks! I found the folder. At least now I know where the trash ends up.

From what I understand there is no "Trash" or "Recycling Bin" in Ubuntu NBR. Maybe the developers forgot to put that option. Strange though, especially since its designed for the mass market (future ex-windows users like me).

But with the path, I can manage it manually.

---

### Post by e-Gee on 2009-12-04
When you are in nautilus (when you click on any folder) you will see trash it is under floppy drive

---

### Post by Jim_in_Germany on 2009-12-04
As an afterthought:

You can also install the "Screenlets" package with :
sudo apt-get install screenlets
and select to have a trash can on the desktop (a nice big automated one)

Or, if you press alt+f2, then type in gconf-editor
then navigate to apps -> Nautilus -> Desktop, you can place a tick by trash_icon_visible, which will then also show a trash can on the desktop

---

### Post by sebastianfaunes on 2009-12-04
Great Info. But that's what NBR users should avoid doing. I tried that, and then I could not get into any folder at all. I almost thought I was going to end up doing a clean reinstall.

But, I've heard that works for regular ubuntu distros

---

### Post by Jim_in_Germany on 2009-12-04
I don't use Ubuntu NBR myself, but that sucks! 
Not finding where your files have ended up if you want to undelete them is a pain in the butt.

---

### Post by sebastianfaunes on 2009-12-04
That dosen't seem to work. But I can find trash in the Go tab. Yet, when i open it the program hangs.

For now the only workable has been to go straight to the folder path

---

### Post by ajgreeny on 2009-12-04
You could always, I assume, manually make a link to the trash folder and put it on your desktop.  Perhaps that is better than the gconf-editor way of doing it, though I have no idea why it should make any difference.

---

