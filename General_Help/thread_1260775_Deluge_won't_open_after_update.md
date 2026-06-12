---
title: "Deluge won't open after update"
date: 2009-09-08
forum: General Help
---

### Post by jono2009 on 2009-09-08
Did a fresh install of Kubuntu 9.04 yesterday with every thing installed and updated, later I started using Deluge(note: I had to drag the  movie torrent into Deluge as I wasn't able to select it/transmission Bittorrent is preselected)  and it downloaded all night. 

This morning after further updates for Ubuntu and a reboot I released if I r/clicked a torrent/properties I could select Deluge...anyhow I then tried to use Deluge and now it won't open. I've fully removed it with Ubuntu Tweak, Synaptic Package Manager and removed finally traces in Home Folder/config...done a fresh install using Ubuntu Tweak, but still get a blank Deluge like this Screenshot

thanks for any help you can give me...

---

### Post by lovinglinux on 2009-09-08
I believe it could be two things:

1 - Deluge gtk interface is not properly connecting to the daemon, so the interface launches but stall without displaying anything

2 - There are two dependencies missing that can be installed manually to fix this issue. The problem is that I don't remember which packages they are. I'm trying to find out the Deluge forum.

Meanwhile, you could try to update Deluge to the latest version using it's [PPA repository](https://launchpad.net/~deluge-team/+archive/ppa) or installing the [deb file](http://www.getdeb.net/app/Deluge).

---

### Post by Vaphell on 2009-09-08
i had similar problem yesterday with my PPA version, but the weird thing was there were no updates recently. It just stopped working when i tried to add torrent to download list.
Deluge run from terminal froze at connecting to localhost:xxxxx daemon
i googled, ubuntuforumed... no dice.
I rebooted and Deluge works again. I don't like that kind of magic :/

---

### Post by lovinglinux on 2009-09-09
> **Vaphell said:**
> i had similar problem yesterday with my PPA version, but the weird thing was there were no updates recently. It just stopped working when i tried to add torrent to download list.
Deluge run from terminal froze at connecting to localhost:xxxxx daemon
i googled, ubuntuforumed... no dice.
I rebooted and Deluge works again. I don't like that kind of magic :/

I wouldn't worry that much. It's probably just a connection issue. If you block the daemon with the firewall and launch Deluge it will do the same thing.

---

