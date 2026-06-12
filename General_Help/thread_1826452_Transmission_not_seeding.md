---
title: "Transmission not seeding"
date: 2011-08-16
forum: General Help
---

### Post by TomAwezome on 2011-08-16
I'm having a small issue with Transmission.
(I am running Ubuntu 11.04)

 Every time I attempt to download a torrent, it will download fine, though I could do some minor improvements. The problem I am having is that once it finishes, the torrent will just sit there and say "Seeding to 0 of 0 connected peers" when I am sure as hell there are peers to seed to.

 I have done this with multiple torrents and they all seem to do the same thing. Any ideas?

---

### Post by SOME1 on 2011-08-16
check if your port open. 
you can check it with [this page]("http://canyouseeme.org/") for example.

---

### Post by TomAwezome on 2011-08-16
No, the port it's on is not open. I have it set to select a random port on startup, is there a specific port I need to set it to? As far as I know, I can't seem to find any open ports to use.

---

### Post by claracc on 2011-08-17
When you select in transmission a random port to share the downloading file you have to open this port to let the traffic in.

You can do this through gufw the gui of ufw firewall. You select add rules and let the traffic in from the port's number settled in transmission.

---

