---
title: "I messed up something..."
date: 2010-03-17
forum: General Help
---

### Post by thefallofroy on 2010-03-17
I'm going to try and explain this the best I can:
I was on Ubuntu last night, and I kind of went crazy with Synaptic and downloaded a bunch of games. I don't know what I did, but I had to have messed up somewhere along the lines, because now whenever I click on the Applications button at the top left, it doesn't show the whole menu like it's supposed to. It just shows a really thin white line underneath, and I can't access the menu at all. I don't know if this will help the matters at all, but for what it's worth, as I was downloading the games I started running out of free space for the partition. And also, I am dual booting between Vista and Ubuntu. I installed Ubuntu on the main C: partition so it shares the hard drive with Vista. I don't know what I did, I tried uninstalling some of the things I installed, and I even restarted. But it still didn't work. Need help. Any ideas?

---

### Post by j7%&lt;RmUg on 2010-03-17
First, right click on your applications menu and click "Edit Menus", if you see all the categories and entries in the dialog that pops up then you have screwed something up.

---

### Post by thefallofroy on 2010-03-17
I believe I tried that, I right clicked on it and clicked edit menus, and nothing came up... So you're saying if something does come up, then that's bad. So how about with this, if nothing comes up?

---

### Post by thefallofroy on 2010-03-17
Bump

---

### Post by lhowaf on 2010-03-17
You could try going to .config/menus, rename your applications.menu to something like applications.menu.saved and copy your latest undo file (applications.menu.undo-xx) to applications.menu.

---

### Post by thefallofroy on 2010-03-17
> **lhowaf said:**
> You could try going to .config/menus, rename your applications.menu to something like applications.menu.saved and copy your latest undo file (applications.menu.undo-xx) to applications.menu.

Could you possibly explain a little more in detail what you mean? I don't quite understand.

---

### Post by lhowaf on 2010-03-17
Sorry. Try this
open a terminal and change to the .config/menus folder:
cd .config/menus

If you list the contents (ls), you'll see a file named applications.menu and one or more "undo" files named applications.menu.undo-xx (where 'xx' is a number).
Type:
mv applications.menu applications.menu.saved

Then, using the name of the highest-numbered undo file ('12' for example) type this:
cp applications.menu.undo-12 applications.menu

Not sure but you might have to log out and back in before you see a change.

---

### Post by lhowaf on 2010-03-17
Reading elsewhere, somebody reported deleting applications.menu works. Of course, renaming it is safer.

---

### Post by nerdy_kid on 2010-03-17
create a new user and see if the problem is still there.  If it is i wouldnt reboot if i were you (unless you already have) cause you could (not sure) end up with nothing but a commandline.

also if your running out of space i would run

```

sudo apt-get clean

```
this will clear out the package cache.  (when you install apps, ubuntu downloads the files and then installs them without deleting the downloaded files.  This makes reinstalling programs fast as you dont have to redownload the packages, but eats space.)

---

### Post by thefallofroy on 2010-03-17
> **lhowaf said:**
> Sorry. Try this
open a terminal and change to the .config/menus folder:
cd .config/menus

If you list the contents (ls), you'll see a file named applications.menu and one or more "undo" files named applications.menu.undo-xx (where 'xx' is a number).
Type:
mv applications.menu applications.menu.saved

Then, using the name of the highest-numbered undo file ('12' for example) type this:
cp applications.menu.undo-12 applications.menu

Not sure but you might have to log out and back in before you see a change.

I tried that, but in my directory no such "undo files" are in there. When i listed the contents the only two things in there were applications.menu and settings.menu

---

### Post by thefallofroy on 2010-03-17
Alright never mind, I dont know what I did, but it's fine now. Do you think the "sudo apt-get clean" fixed it?

---

### Post by nerdy_kid on 2010-03-18
never run into low disk space on ubuntu before, so i dont know what kinda quirks arise, but if the problem was indeed low disk space then yeah, it fixed it ;)

---

### Post by thefallofroy on 2010-03-19
Thanks for all your help guys

---

