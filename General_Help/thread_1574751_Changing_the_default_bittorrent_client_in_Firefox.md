---
title: "Changing the default bittorrent client in Firefox"
date: 2010-09-14
forum: General Help
---

### Post by kafka201 on 2010-09-14
I've got both Deluge and Vuze installed on my box and the default in Gnome is set to Deluge which is what I want, but in Firefox the default is set to Vuze so when I download a torrent file and open it through the Downloads window that pops up it opens in Vuze, which is what I don't want.  

I've looked into the preferences file and tried to change the program application but it seems that it's either always ask, save file, use Vuze(default), or use a different program like Deluge.  I like it to always ask, so I don't want to change it to use Deluge first, I want it to always ask, but then have Deluge be the default.  

Any ideas?

---

### Post by punkideas on 2010-09-22
I'm having the same problem, except with Transmission rather than Vuze.  I've determined that the default setting is inherited from Ubuntu, and it cannot be fixed in Firefox.  Does anyone know where Firefox inherits this setting from Ubuntu, and how it can be changed?  I've already tried changing it in Gnome, and that did not work.

---

### Post by punkideas on 2010-09-22
I figured it out.  You need to add or change a line in /etc/gnome/defaults.list
First,
```
gksudo gedit /etc/gnome/defaults.list
```If there is a application/x-bittorrent= line, change it to the following.  Otherwise, add it.
```
application/x-bittorrent=deluge.desktop
```Then restart Firefox, and it will change the default

---

### Post by ninjapirate89 on 2010-09-22
I just save .torrent files and have Deluge monitor my Downloads folder for .torrent files and automatically add them.

---

### Post by kafka201 on 2010-09-24
Thanks punkideas it worked.

And I have quite a few different .torrents set up in the same folder that I only activate sporadically, so your idea wouldn't really work for me ninjapirate, thanks for the response though.

---

### Post by CommuneOfLoon on 2012-02-20
> **punkideas said:**
> I figured it out.  You need to add or change a line in /etc/gnome/defaults.list
First,
```
gksudo gedit /etc/gnome/defaults.list
```If there is a application/x-bittorrent= line, change it to the following.  Otherwise, add it.
```
application/x-bittorrent=deluge.desktop
```Then restart Firefox, and it will change the default

When I went to the application list, there is nothing for bittorents, any ideas?

---

### Post by CommuneOfLoon on 2012-02-20
Nevermind. I went to terminal and typed 'which deluge' which gave me the path to the program. In Firefox I chose 'other' instead of Transmission and typed in the path, since for some reason Deluge is not coming up in the /bin folder. Seems to have kept Deluge as the default since I did that.

---

### Post by oldos2er on 2012-02-20
Back to sleep. Closed.

---

