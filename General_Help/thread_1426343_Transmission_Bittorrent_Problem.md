---
title: "Transmission Bittorrent Problem"
date: 2010-03-10
forum: General Help
---

### Post by dkstoney on 2010-03-10
When I try to open Transmission, or try to download a new torrent, I get the following Gnome message:

> Transmission cannot be started.
Couldn't open "/home/dkstoney/.config/transmission/lock": Permission denied3 folders, which are bit-torrents in progress, in my Downloads folder have lock icons on them. Under Properties, they are owned by root. Other completed torrents do not have locks.

I had a system update last night. I wasn't running Transmission. I shut down shortly afterwards. I came home from work today and tried to start.

This program has been running fantastically and I've been very pleased with it. I used to use utorrent on Windows XP and I have recently converted to Ubuntu, so I'm a total noob.

Please help.
Thx

---

### Post by kerry_s on 2010-03-10
there not suppose to be owned by root, did you run transmission as root?

i would open the file manager as root & delete them.

press-> alt+f2
type-> gksudo nautilus /home/dkstoney/.config/transmission

---

### Post by geirha on 2010-03-10
Nah, deleting shouldn't be necessary, just change ownership back to yourself.

```
sudo chown -R "$USER:$USER" ~/.config/transmission
```

---

### Post by dkstoney on 2010-03-10
> **geirha said:**
> Nah, deleting shouldn't be necessary, just change ownership back to yourself.

```
sudo chown -R "$USER:$USER" ~/.config/transmission
```

Thanks much, geirha!!!

That worked and my problem is solved. Do you suppose it was the update?

---

### Post by geirha on 2010-03-10
I hope not. Updates, or packages in general, should never ever change anything in any homefolder. 

Not sure what could've caused it.

---

### Post by dkstoney on 2010-03-10
Now, how do I gain ownership of the folders?

---

### Post by geirha on 2010-03-10
> **dkstoney said:**
> Now, how do I gain ownership of the folders?

You just did. That chown command made you the owner of ~/.config/transmission and all files and folders below it.

---

### Post by dkstoney on 2010-03-10
I looked it up and figured it out. Nevermind, I'm good to go. Thx again.

---

