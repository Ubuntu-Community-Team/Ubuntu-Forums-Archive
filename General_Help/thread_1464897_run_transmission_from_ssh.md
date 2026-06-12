---
title: "run transmission from ssh?"
date: 2010-04-28
forum: General Help
---

### Post by randumnumber on 2010-04-28
I have a media server at home, it has transmission on it. I need to be able to start transmission from somewhere else over SSH, I have tried to do ssh -X and run it, but of course it opens up transmission on my current computer. I have tried to just run transmission from a regular ssh session and it says it Cannot open display, i have tried to run it with the & sign and it still wont stay open....

How do i run a program from ssh so that it opens on the remote computer and stays open while i do other things?

---

### Post by _0R10N on 2010-04-28
I think this is not possible, because every process we launch from a console is bound to that console. In this case, the program that you run remotely is bound to the terminal being opened when your ssh session starts.

The best way I know to accomplish what I think you want (start a process remotely and letting it running) is though a Remote Desktop application. Ubuntu is bundled with the Remote Desktop Viewer. The problem with this approach is that it will require some configuration on the system that you're trying to access. Not too hard, but anyway, I can give you a hand if you get stuck.

Kind regards!

_0R10N >>

---

### Post by marshmallow1304 on 2010-04-28
You could also use a cli-based torrent client, like rtorrent.

---

### Post by 3rdalbum on 2010-04-28
Transmission also comes as a daemon - "transmission-daemon". You can enable a web-based interface that's built-in (called Clutch) so you can manage torrents from any computer on the network.

Transmission Daemon will start as soon as you install the transmission-daemon package.

---

### Post by Serpher on 2010-04-28
You can edit the file /etc/ssh/ssh_config and pretty much just change anything with "X11" somewhere in the variable to "yes". When you're done that, in ssh just type in tranmission. I don't believe X11 has to be running on the computer you're SSH'd into.

Here's some more detail: [http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

---

### Post by Dayofswords on 2010-04-29
you could also just use deluge, which separates its client and daemon so you can do CLI or GUI

it has does a thin client mode so you can use deluge client from elsewhere and connect to it (it can do SSH tunnelling, takes more setup steps though

there is also a webui that can do ssl

going to cli you will have to get "deluge-console" package after you get the "deluge" package

for webui, i think you'll need "deluge-webui"

---

### Post by randumnumber on 2010-04-29
Deluge sounds like the proper way to go, even though it is a round about way of getting what I want. I might just install transmission as a headless setup and configure the webui so i dont have to worry about a gui anymore. Thanks! Now how do i mark this as solved?

---

### Post by jerome1232 on 2010-04-29
Thread Tools-> Mark as Solved.

---

### Post by dragos2 on 2010-04-29
What about run it through ssh -X then disconnect network ?
Better options already posted but who know who will find this useful.

---

### Post by randumnumber on 2010-04-29
> **dragos2 said:**
> What about run it through ssh -X then disconnect network ?
Better options already posted but who know who will find this useful.

I tried this, Transmission is still bound to the shell i create with ssh, so when i close the terminal it breaks the connection.

---

### Post by andrew.46 on 2010-05-10
Hi randomnumber,

> **randumnumber said:**
> I tried this, Transmission is still bound to the shell i create with ssh, so when i close the terminal it breaks the connection.

I use rtorrent with screen for exactly this reason, I imagine this would also work with the cli form of transmission?

All the best,

Andrew

---

### Post by Charles Kerr on 2010-05-12
You can use transmission-daemon + one of the many remote controls to leave transmission running headless and connect to it via a remote.  That way you don't even need to have a terminal.

But to answer your question of how to run it in a terminal even when you're not logged in: "screen" is the application you're looking for.  You run the terminal inside of screen, then detach and reattach.  I use this to connect from various places to a continuous irssi session I have running on one machine inside of screen.

---

### Post by alecz20 on 2010-08-24
> **3rdalbum said:**
> Transmission also comes as a daemon - "transmission-daemon". You can enable a web-based interface that's built-in (called Clutch) so you can manage torrents from any computer on the network.

Transmission Daemon will start as soon as you install the transmission-daemon package.

Unfortunately the web-interface doesn't work for adding torrents in version 1.51 (9.04)

---

