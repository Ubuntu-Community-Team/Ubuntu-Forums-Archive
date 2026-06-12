---
title: "Ubuntu boots to terminal."
date: 2006-05-21
forum: General Help
---

### Post by BigglesTheGreat on 2006-05-21
Hi there, today I successfully installed Ubuntu and spent the entire day customising the OS and enjoying adjusting to a new interface.

Then this evening I went to restart the computer and it now refuses to boot the graphic interface and instead loads:

```
Ubuntu 5.10 "Breezey Badger" Ubuntu tty1

Ubuntu Login:
```

The last thing I did that I assume did it was play around with aMSN attempting to enable the sound.
The very last command I ran was ```
sudo apt-get install esound-clients
``` which appeared to remove many packages. After it had finished, over half of my installed programs were missing from the applications, admin and preferences menus.

I need some help to get the interface back up and running.
Please excuse any incorrect terminology, I'm new to Linux.

---

### Post by Kethinov on 2006-05-21
Is xorg crashing? If so, you need to post the contents of **/var/log/Xorg.0.log** so we can help you fix it.

---

### Post by BigglesTheGreat on 2006-05-21
Not quite sure how to do that or what xorg is...

---

### Post by Kethinov on 2006-05-21
Do you have another computer handy or another OS on the computer with which to retrieve the file easily?

---

### Post by BigglesTheGreat on 2006-05-21
Only Ubuntu is installed on the system, I'm using a Windows computer to post.

---

### Post by Kethinov on 2006-05-21
If you have a Linux LiveCD of some sort to boot that computer with, such as the Ubuntu one, Knoppix, or some other one, you could boot it, open the file in a text editor, and post it here from there.

Or you could network your Ubuntu machine to your Windows machine and setup a Samba share so your Windows machine can grab the file. The first option is easier, but if you don't have a LiveCD, I can walk you through setting up Samba from the terminal.

---

### Post by BigglesTheGreat on 2006-05-21
I ran "sudo apt-get install ubuntu-desktop" and everything is back to normal.

Any idea why "sudo apt-get install esound-clients" removed so many things including the desktop interface?!

---

### Post by Kethinov on 2006-05-21
It's possible that one of its dependencies conflicted with a lot of major packages. For example, you will have similar problems if you try to install hotplug in Dapper.

Glad you got it fixed.

---

