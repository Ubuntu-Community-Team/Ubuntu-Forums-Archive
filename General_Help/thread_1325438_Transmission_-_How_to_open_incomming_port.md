---
title: "Transmission - How to open incomming port??"
date: 2009-11-13
forum: General Help
---

### Post by Kaffekop on 2009-11-13
ok I'm trying to download a pdf file torrent via Transmission BitTorrent Client.

It looks like my firewall is blocking all incomming ports, and I don't get a THING of how it works (tried to figure it out in terminal > man ufw, but im totally lost just looking at it..)

Can somebody explain me what to write in the terminal to possibly fix this?

Second problem (thought it might have something to do with the firewall though) is that I get the error:
"Tracker gave an error: "unregistered torrent""

Thanks for taking your time :)

---

### Post by Boondoklife on 2009-11-13
Well I dont think, unless you have setup a firewall yourself, ubuntu blocks anything by default. This is most likely up the pipe in your router or ISP, you can check by using:
```
sudo ufw status verbose
```
there is also a gui in the repos: gufw

---

### Post by lovinglinux on 2009-11-13
See the troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by nerdy_kid on 2009-11-13
i am pretty sure that ufw is disabled by default on ubuntu -- run
```

sudo ufw disable

```

and see if that works.  If not, it is probaly your router's firewall;
1.  check Use UPnP in transmission options, if that doesn't work then
2.  enable UPnP from router's config.  (you can get to this by typing in a web address bar 192.168.1.1)


hope this helps

---

### Post by Kaffekop on 2009-11-13
thanks for replying, I disabled it now but it did'nt help much. I tried in Vuze and that did'nt work either. I guess it is my routers firewall, but I have no idea how to fix that..

---

### Post by lovinglinux on 2009-11-13
> **Kaffekop said:**
> thanks for replying, I disabled it now but it did'nt help much. I tried in Vuze and that did'nt work either. I guess it is my routers firewall, but I have no idea how to fix that..

See the troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

