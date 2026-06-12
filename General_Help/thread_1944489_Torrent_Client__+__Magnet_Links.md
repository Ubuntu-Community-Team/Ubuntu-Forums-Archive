---
title: "Torrent Client  +  Magnet Links"
date: 2012-03-21
forum: General Help
---

### Post by matt.k on 2012-03-21
Hi 

I have done a bit of searching on here already and I cant find what im looking for.

Basically I own a share in a server somewhere out the way which has ubuntu server on it, which works great. I would normally SSH into my server and use rTorrent to download my files but now that some sites are starting to use magnet links I can't get it to work; so what i'm really asking is if there is a different torrent client with or without a webui I can use to download magnet links. A tutorial would also be very helpful thanks.

(sorry if this is in the wrong section)

---

### Post by LewisTM on 2012-03-21
qbittorrent supports magnet links and provides an interesting WebUI.

You could run it with X forwarding but that would be slow and unreliable over SSH. Best use the command line service [qbittorrent-nox]("http://sourceforge.net/apps/mediawiki/qbittorrent/index.php?title=Running_qBittorrent_2_without_a_X_server") (found in a separate package).

What you do is spawn the daemon inside a remote GNU screen session (running inside your SSH session),
```
screen qbittorrent-nox
```
and detach the session with Ctrl-A, D
Use SSH to forward the webUI port (typically 8080)
```
ssh -L 8080:localhost:8080 user@yourserver
```
Then connect to the WebUI at [http://localhost:8080](http://localhost:8080)
Don't forget to keep the SSH session active if you want to manage torrents. However, if your SSH dies, the daemon will still be alive because it was started in a persistent screen session. That means downloads etc. will continue.
Don't forget to set the options in the UI on first use: user, password, locations, etc.

Cheers!

---

### Post by papibe on 2012-03-21
transmission-daemon works pretty well on a server with no GUI. It can be turn on and off as a regular service. It is has a webGUI and works perfectly with magnet links.

[Here]("http://www.vanutsteen.nl/wp-content/uploads/2008/12/transmission_screenshot.png")'s a pic of the webGUI, and [here]("http://1000umbrellas.com/2010/10/04/updated-transmission-installationconfiguration-on-ubuntu-server") is a little tutorial.

Hope that helps,
Regards.

---

### Post by ksa618 on 2012-03-21
I think newer versions of rtorrent support magnet links.

---

### Post by pyroscope on 2012-03-21
[http://wiki.rtorrent.org/MagnetUri](http://wiki.rtorrent.org/MagnetUri)

0.8.9 does.

---

### Post by Cheesemill on 2012-03-21
I run Deluge as a daemon on my server and connect using the Deluge GTK client on my workstation.

---

### Post by HiImTye on 2012-03-21
I would assume that rtorrent would be the best option since it's headless to begin with, while the others have graphical front ends and web based access secondary

---

### Post by Cheesemill on 2012-03-21
> **HiImTye said:**
> I would assume that rtorrent would be the best option since it's headless to begin with, while the others have graphical front ends and web based access secondary

Deluge is slightly different. The deluge-daemon package is headless and runs CLI only. You then connect to this daemon using the standard GTK client.  I like this because Deluge was always my bittorrent client of choice anyway, so I get to use the same familiar interface but just have it communicate with a headless server instead of running entirely on my workstation.

---

### Post by matt.k on 2012-03-22
> **Cheesemill said:**
> Deluge is slightly different. The deluge-daemon package is headless and runs CLI only. You then connect to this daemon using the standard GTK client.  I like this because Deluge was always my bittorrent client of choice anyway, so I get to use the same familiar interface but just have it communicate with a headless server instead of running entirely on my workstation.

Hi thanks for the reply, I installed deluge and im running the the webui (which is very nice) but I think i might of somehow installed an old verstion of it, is their some way i could update it or should i just reinstall it? If so could you possible tell me the correct way to reinstall it or point me in the right direction (looked at there site but no help was found for server side).
Thanks again

---

### Post by Cheesemill on 2012-03-22
There is a PPA containing the latest version here:
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

---

### Post by nmlferreira on 2012-03-24
Hello,

I've recently installed Transmission 2.33.
Do you know if this version supports magnet?

Thanks.

---

### Post by kdane4 on 2012-03-24
> **nmlferreira said:**
> Hello,

I've recently installed Transmission 2.33.
Do you know if this version supports magnet?

Thanks.

hi.

yes, I think since version 1.8 it started having support for magnet links.

---

