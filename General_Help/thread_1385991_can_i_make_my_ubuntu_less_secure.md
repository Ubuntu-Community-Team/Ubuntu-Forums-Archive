---
title: "can i make my ubuntu less secure?"
date: 2010-01-20
forum: General Help
---

### Post by Søren on 2010-01-20
hey all.

is there any way i can chnmod my whole installation? is there some super admin setting that i can log into and change so I dont have to keep chmoding foles all the time whenever i want to delete, change, more or create a file in a protected directory? its great that ubuntu is very secure and all, but my computer sits in my room with only me using it and i am not guarding secrets. its gets pretty tedious having go to the command line whenever i want to create a file in home or wherever. can i just chmod the roots directory? will that trickle down the tree?

---

### Post by x33a on 2010-01-20
you should be able to do anything in your home dir without root privileges. as for the other folders, messing around with permissions isn't the best thing to do, as it is not a good practice for a linux user in general and might even break something on your system.

---

### Post by epicoder on 2010-01-20
You probably can by doing this:

```
sudo chmod --no-preserve-root -R go+rwx /
```This will make your filesystem and EVERYTHING mounted on it readable, writable, and executable by all users, so unmount anything you don't want to affect. I wouldn't reccomend doing it, though.

You don't have to go to the terminal to create folders in things above your home directory. Create a custom launcher on your panel with this command:
```
gksudo nautilus %f
```
This will launch a file browser with root permissions, so be careful with it.

---

### Post by nothingspecial on 2010-01-20
I wouldn`t do it if I were you.

---

### Post by 3rdalbum on 2010-01-20
> **Søren said:**
> hey all.

is there any way i can chnmod my whole installation? is there some super admin setting that i can log into and change so I dont have to keep chmoding foles all the time whenever i want to delete, change, more or create a file in a protected directory? its great that ubuntu is very secure and all, but my computer sits in my room with only me using it and i am not guarding secrets. its gets pretty tedious having go to the command line whenever i want to create a file in home or wherever. can i just chmod the roots directory? will that trickle down the tree?

My dear fellow, you're doing things the wrong way. You don't chmod directories just so your user account can modify them!* You run the modifying program as root. The easiest way to do that is to type in the following command:

```
gksudo nautilus
```

which runs your file browser as root, so you can do whatever you want to do within that window, include copying files in. And if you double-click on a file, it will also open as root.

Of course, only run that command when you actually need to be root.

There's actually an even better way: Install the "nautilus-gksu" package from Synaptic. When you next login, you can right-click on any file or folder and choose "Open as Administrator". Easy! No terminal use required!

Chmodding the entire filesystem so it's writable by your user account is really bad. It makes it possible for program executables to become corrupt just like in Windows. It allows remote security flaws in programs to become potentially very serious. And it could break your system straight away. And Murphy's Law, as soon as you chmod your entire system you'll accidentally delete something crucial that you wouldn't have done if you'd had to open a root file browser.

* It's not your fault - I've seen a handful of people telling new users that they must chmod files and directories before they can modify them. It's not good advice and I've always tried to steer those new users back on the correct path, but I don't check up on the forums 24/7.

---

### Post by lotharmat on 2010-01-20
Danger Will Robinson - Danger

---

### Post by BbUiDgZ on 2010-01-20
> **søren said:**
> hey all.

Is there any way i can chnmod my whole installation? Is there some super admin setting that i can log into and change so i dont have to keep chmoding foles all the time whenever i want to delete, change, more or create a file in a protected directory? Its great that ubuntu is very secure and all, but my computer sits in my room with only me using it and i am not guarding secrets. Its gets pretty tedious having go to the command line whenever i want to create a file in home or wherever. Can i just chmod the roots directory? Will that trickle down the tree?
lol?

---

### Post by fromthehill on 2010-01-20
chmodding your entire filesystem will result in making it unbootable

I did it once
it has kind of the same effect as pulling out the harddrive :P

---

### Post by iponeverything on 2010-01-20
Doing that recursive chmod will break your system.

---

### Post by fromthehill on 2010-01-20
> **iponeverything said:**
> Doing that recursive chmod will break your system.
it will make his system more secure though :D

---

### Post by ajgreeny on 2010-01-20
DO NOT DO IT!!!

It will be a disaster and almost impossible to retrieve your OS from such a drastic step. Lots of files **must** have specific permissions for them to work properly, and they're not all the same, so you can't even undo what you did with another single command because you will not know what the permissions were before you did the deed.

Install **nautilus-gksu** and you can right click any file or folder and open as administrator.  It makes life so much simpler even than using *gksudo nautilus* in terminal.

---

### Post by wojox on 2010-01-20
May I ask why out of curiosity?

---

### Post by Søren on 2010-01-20
ha ok. thank you all. very helpful community, i must say.

fyi, i was already aware of the gksudo nautilus command. however, since i always find myself opening and closing windows, having numerous windows open, and sometimes getting into a disorganized state, i still find myself typing gksudo nau.. dozens of times per session which is more effort than id like.

anyway, im going to follow the advice given by 3rdalbum and have an admin option installed on by desktop or through synaptic.

ive been finding ubuntu frustrating at if first but im starting to see that its a trade off for flexibility and might be easier than mac/windows once i learn to make it work for me.

cheers

---

### Post by fromthehill on 2010-01-20
you can also make a launcher or a menu entry with the command "gksu nautilus"
that way you only have to click once

---

### Post by Leppie on 2010-01-20
if you want everything with root permissions, you could also use recovery mode to boot.
otherwise you could open a root shell in terminal:
```
sudo -i
```

---

