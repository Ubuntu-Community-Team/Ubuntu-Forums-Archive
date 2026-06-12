---
title: "Best torrenting app for a headless server"
date: 2009-07-06
forum: General Help
---

### Post by talsemgeest on 2009-07-06
Hi, I have just built a headless server, and I would like it to take over my torrenting from my windows machine. So, here is what I need:


[LIST]
[*]Web based interface
[*]Option to force a recheck on downloaded files.
[*]Scheduler to start downlaods at a certain time and stop at another, every day. However, it should also have the option to force start the torrent and ignore the scheduler.
[/LIST]
So, does anyone have any ideas about a suitable application?

Thanks in advance :)

---

### Post by prshah on 2009-07-06
> **talsemgeest said:**
> Hi, I have just built a headless server, and I would like it to take over my torrenting from my windows machine. 

I highly recommend rtorrent; has everything you need except a web-based interface.

The interface is command line, and it has these advantages:

a) You can control it over SSH
b) You can use a GPRS capable phone with an SSH client, and then use that to control your torrentbox wherever you are.

---

### Post by talsemgeest on 2009-07-06
> **prshah said:**
> I highly recommend rtorrent; has everything you need except a web-based interface.

The interface is command line, and it has these advantages:

a) You can control it over SSH
b) You can use a GPRS capable phone with an SSH client, and then use that to control your torrentbox wherever you are.
Ok, I will give it a try

---

### Post by kpkeerthi on 2009-07-06
Deluge / Transmission. Both can run in daemon mode.

Transmission has web ui. Deluge has a GTK UI that you can attach to the daemon running on your headless server.

---

### Post by talsemgeest on 2009-07-06
> **kpkeerthi said:**
> Deluge / Transmission. Both can run in daemon mode.

Transmission has web ui. Deluge has a GTK UI that you can attach to the daemon running on your headless server.
Ok, I think I will give transmission a try. However, how do I change the settings from the cli?

EDIT: That is, once I have installed the daemon, what do I need to do to get to the web interface?

---

### Post by lovinglinux on 2009-07-06
> **kpkeerthi said:**
> Deluge / Transmission. Both can run in daemon mode.

Transmission has web ui. Deluge has a GTK UI that you can attach to the daemon running on your headless server.

Deluge beats Transmission by miles. It has remote GTK, webui with different themes, including ajax, and remote cli. It's easy to configure and has most tools you need from a torrent client. 

[http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

### Post by talsemgeest on 2009-07-06
Thanks, I will give it a try as well, as soon as I can.

---

### Post by talsemgeest on 2009-07-08
So far I have tried transmission daemon, and torrentflux. Torrentflux came close, but seems a bit unstable. For now I think I will use Utorrent in a windows vm.

---

