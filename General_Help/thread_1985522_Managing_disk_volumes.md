---
title: "Managing disk volumes"
date: 2012-05-23
forum: General Help
---

### Post by RPGillespie on 2012-05-23
Could somebody briefly outline the steps needed to do the following:

1. Wipe a secondary hard drive so that ubuntu server edition (which is on the primary drive) can use it as storage

2. Get rid of grub so that when I boot up the computer it goes straight to ubuntu server edition instead of the grub menu (the secondary hard drive currently has ubuntu desktop edition on it)

Thanks for the help, it's much appreciated!

RPG

Edit: Is is possible to have the file server set up to spill into the secondary hard drive if the primary one fills up? How would I go about doing that? 

Is there any good reading material about this kind of stuff or do I just have to learn by experimentation?

---

### Post by Sidewinder1 on 2012-05-23
First, I'd back up the primary and any data that you might want to save from the secondary. Then simply format the secondary (ext3 or ext4). Make certain your formatting the correct drive. Once you reboot, I think GRUB will only list the server
edition on the primary; if not, from terminal just type:
```
sudo update -grub
```
That should do it..

Side

---

### Post by ajgreeny on 2012-05-23
So are you saying you want to wipe the desktop ubuntu from the secondary disk and just run the server from the primary disk?

If so you can simply use a live CD, or even the command line of your server to format the secondary disk, after backing up any files you need to keep.

Where is the grub that you are currently using getting its configuration from, because if it uses the desktop OS and you format that out of existence, you will not be able to boot at all.

More info please.

---

### Post by Sidewinder1 on 2012-05-23
Excellent point ajgreeny! I didn't even consider if grub is on the secondary drive; that would require a re-installation of it on the primary. Nice catch.
{Side hits himself in the head with a shovel.}

---

