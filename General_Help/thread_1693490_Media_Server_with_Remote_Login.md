---
title: "Media Server with Remote Login"
date: 2011-02-22
forum: General Help
---

### Post by ValdeEdius on 2011-02-22
Ok so here is my scenario:

[LIST]
[*]I have a media server running windows 7, I want to change it to Ubuntu 10.10
[*]Server currently configured to Allow Multiple Logon so that the primary display is sent to the TV it is attached to, and when I use Remote Desktop to connect (over ssh) it creates a second copy of the active account (it could be another account, doesn't matter) and that account exists without disconnecting the current user or allowing the current user to see what the Remote Desktop user is doing.
[*]Current server has an ssh server installed
[/LIST]
So I am capable of installing the linux server, but to get windows to allow me to log in the way I do was tricky business. Since I am going to swap the hard drive configuration around soon and would have to re-install windows anyway, I want to play with linux on this server. If for no other reason than a Samba server and a functional VPN.

Now, my only concern is that multiple login thing. It is crucially important that I am able to log in as a kind of "background" user. A media server doesn't do anyone much good if in the middle of a movie someone logs on and starts beating around in some config files and has no idea that someone is on the couch watching tv after all.
So my question is, does anyone know of a way about configuring such a "background" login. It needs a full GUI, the active user should not be able to see (or hear) anything that happens, the account should be able to remain active after the remote client disconnects and wait around for a reconnect, allowing all the programs to run like normal in the meantime.

---

### Post by ValdeEdius on 2011-02-23
bump

---

