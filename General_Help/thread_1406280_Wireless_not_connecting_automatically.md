---
title: "Wireless not connecting automatically"
date: 2010-02-13
forum: General Help
---

### Post by Old *ix Geek on 2010-02-13
After installing 9.10 (clean install of the OS), each time I restart my laptop I have to "OK" the wireless connection prompt in order for it to activate. The prompt that appears is the 'wireless security' tab of the 'network connection' window--with EVERYTHING filled in as it should be.

**YES, I DEFINITELY have "connect automatically" checked.** :)

Any ideas? :confused:

---

### Post by Old *ix Geek on 2010-02-14
Got everyone else stumped, too, eh?

---

### Post by Satoru-san on 2010-02-14
Can you take a screenshot? It is hard to picture, I dont use KDE I use Gnome, but I have used kde-4 before, so I might be of help.

---

### Post by Old *ix Geek on 2010-02-14
Here's a screenshot of what I'm seeing immediately after rebooting and logging in:

[img]http://www.smartassproducts.com/images/ubuntu_forum/UbuntuForum.jpeg[/img]

The ONLY thing I have to do is hit "OK," so it's not like the stored password is wrong or anything like that.

I've done a little experimenting, though. I decided to log in using GNOME instead of my usual KDE, just to see if something there would shed any light on the situation.  It did, sort of.  Immediately upon restarting/logging in, I got a prompt for the default keyring's password, with the message that NetworkApplet (/usr/bin/nm-applet) needed the keyring but it was locked. As soon as I entered its password, the wireless connection proceeded to connect.

Note that within their respective wallet managers (KDE and GNOME), access control for KNetworkManager and NetworkApplet are set to "Always allow."

---

