---
title: "Bittorrent Client"
date: 2006-02-17
forum: General Help
---

### Post by MA! on 2006-02-17
I have set up breezy server instalation on an old machine. I administrate it with ssh from my windows machine via tool called "putty". 
I **wget** for a torrent file and then do **btdownloadcurses** (btw whats the diffrence between **btdownloadcurses** and **btdownloadheadless** ?) everything fine, file sarts downloading, but when i close putty it stops downloading.
So how to make it donwload even if im not logged in ?

---

### Post by Leif on 2006-02-17
preface your command with "nohup"

---

### Post by bored2k on 2006-02-17
[QUOTE=MA!]
So how to make it donwload even if im not logged in ?[/QUOTE]
**btdownloadheadless - **Downloads torrents in the same manner as btdownloadcurses or btdownloadgui, but does not require a terminal to stay alive. [http://linux.com.hk/penguin/man/1/btdownloadheadless.bittornado.html](http://linux.com.hk/penguin/man/1/btdownloadheadless.bittornado.html)

---

### Post by MA! on 2006-02-18
Thanks nohup works well.
But how do i display how far the download proceeded ?

And whats the diffrence between the package "bittorrent" and "bittornado" . 
They seem to have completly same commands, execept of file endings (.bittornado and .bittorrent)

Edit:There is a "nohup.out" file.
how do i open it ?

---

