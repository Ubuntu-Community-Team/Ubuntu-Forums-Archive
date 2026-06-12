---
title: "Accessing my http site through https"
date: 2011-10-27
forum: General Help
---

### Post by nLinked on 2011-10-27
I'm using the open source Motion CCTV/webcam software to allow me to view my camera live over a network. Internally, I can go to my web browser, type in the URL which is something like [http://nameofmyubuntuserver:8081](http://nameofmyubuntuserver:8081).

That will take me to my camera's live feed.

Now I could port forward that to access it remotely, but there's the potential of someone seeing that address by something like analysing packets.

Is there any way to secure that address? I'm running Motion on Ubuntu Server 11.04.

Preferably I'd like to make it go through https as well as prompt for a password. I found [this]("http://www.lavrsen.dk/foswiki/bin/view/Motion/SecureWebcamFeeds") but it seems so complex. Is there an Ubuntu package which can allow me to access that address after authenticating myself and encrypting the connection? It doesn't even have to be Motion-specific. I'm just looking for an easier way to encrypt and authenticate a locally-hosted http site.

Or even better, an Ubuntu package that creates me a new website with authentication and https (preferably something simple, Apache scares me), which then redirects to my local site in a secure manner?

---

### Post by gsmanners on 2011-10-27
If you know the remote IP address, you could always whitelist it using [UFW]("https://help.ubuntu.com/community/UFW") (or use Ekiga if you want a really simple solution).

---

### Post by nLinked on 2011-10-27
And this is why I love this community!

So you mean I can deny all access to port 8081 using ufw on my server, except for say my LAN addresses and the host name of my Android smartphone (as I'll be accessing the feed via my Android browser)?

Maybe I can change the host name of my phone to something complex. Then when I access the feed, if anyone managed to get the URL, they won't be allowed in (unless they use the same host name).

The problem is someone snooping the connection may be able to get the details.

How can I use Ekiga, and will it work on Ubuntu Server (CLI)?

---

### Post by gsmanners on 2011-10-27
Ekiga is meant to be a desktop app, so I'm not sure that would really work out too great in your setup maybe. But firewall is obviously designed for really basic security. If you know the remote IP you're going to be using, it makes it really convenient for services that you need to be strictly private. It does kind of rely on you having a nice static IP, though.

EDIT: Might be a good idea to look at SSL, in any case:

[https://help.ubuntu.com/11.10/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/11.10/serverguide/C/httpd.html#https-configuration)

---

### Post by nLinked on 2011-10-27
If I use the firewall and assuming I had a static remote IP, is it possible for a snooper to find the IP and spoof it so they can connect with the same static IP as well?

---

### Post by gsmanners on 2011-10-27
I'm pretty sure a MACID can be, but I don't think an IP can be spoofed. (It might depend on how good your ISP is, though.)

---

