---
title: "Headless torrent server"
date: 2010-02-18
forum: General Help
---

### Post by sideaway on 2010-02-18
Hey there guys, setting up a headless torrent server for the flat. The webui works great on transmission except I want to schedule it to pause during daylight hours. Essentially I only want it to be downloading between the hours of 2am and 8am.

Currently I cannot get it to pause. Only throttle the speed. Setting the speeds to zero appears to set it to unlimited speed. And we don't really want it running 1 kb/s constantly (lowest possible setting) during the day.

Server is running 8.04 LTS using Transmission 1.83. Currently I have the Gnome desktop installed and using remote desktop viewer to set some things up via a gui. CLI is faster... if you know what you're doing, which I don't really, so I like to fiddle :P Can anyone help?

I did think about using Crontabs to kill the process at 8am and start it at 2am, however this is pointless as we'd like to be able to setup torrents via the webui during the day.

---

### Post by sideaway on 2010-05-01
Ok buuump. I've currently got Vuze installed, but it's bloated, constantly prompts me to donate and is a PIA to use - and on a headless server I cbf with that - all it's meant to do is sit quietly. BUT. It does have a webui + a comprehensive scheduler (if only via plugin).

I really don't like using vuze and would love something that's lighter and more intuitive that has two features, a comprehensive scheduler and webui. Does anyone know of a torrent program with those features?

---

### Post by coachnatebean on 2010-05-01
How about uTorrent through WINE?
I know it has the capability of limiting downloads during portions of the day.
Maybe rTorrent if you don't want to use WINE?

---

### Post by sideaway on 2010-05-02
Does rTorrent have a web interface? and scheduler? I've downloaded a couple but they don't quite have the functionality I'm looking for.

---

### Post by IanW on 2010-05-02
Deluge can run headless (client/daemon can be installed on separate machines) and has a scheduler plugin available.

---

### Post by Dayofswords on 2010-05-02
> **IanW said:**
> Deluge can run headless (client/daemon can be installed on separate machines) and has a scheduler plugin available.

this.

deluge separates its client and daemon
has a console
has a webui plugin
as he said, a scheduler plugin
blacklist plugin
can do a thin client set up(client on one computer, daemon running on another)
simply awesome

i'm not sure to get webui going =p but you can do it

```
sudo apt-get install deluge deluge-console
```
i think you just need 'deluge-core' for headless, yet to try, but defiently get the deluge-console

---

### Post by sideaway on 2010-05-06
Hey thanks guys trying to setup deluge now :)

---

### Post by Longinus00 on 2010-05-06
Newer versions of transmission (1.90+ I think) will respect 0kpbs settings for speed limits. Transmission also has a daemon version you can install with the transmission-daemon package.

---

### Post by SFSDCris on 2010-05-24
How do you get around situations in which Ubuntu requires input during the boot process?

I have no keyboard or monitor attached my media server which is running Ubuntu. 

I currently have a situation where if there is a problem, Ubuntu stops on boot and asks which system I want to run. 

Secondly, if there is a disk problem, it requires I run a disk check to hit 'y' a bunch of times to approve attempted fixes. 

For a headless, keyboardless media server this is impossible. 

Ideally auto-rebooting after a power failure, auto-attempting to fix disk problems, reporting any errors once ubuntu (successfully) booted.  Is there a way to do this?

---

### Post by sideaway on 2010-05-28
SFSDCris, I hear you, I just don't turn the server off :P

---

### Post by IanW on 2010-06-03
I went with a cheap KVM box as both my PC & server are in the same room.

---

