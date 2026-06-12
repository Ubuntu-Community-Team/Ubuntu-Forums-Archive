---
title: "FreeNX or VNC ?"
date: 2005-01-21
forum: General Help
---

### Post by Ste on 2005-01-21
If I've read things right either of these will let me open remote connections to other pcs.. right ?
My question is how could I connect a winxp home pc to a ubuntu linux pc, so I can transfer files etc to one and the other. Will either of these work or what else should I use ?

The winxp home pc does have zonealarm as a firewall will this be a problem ?
If anyone can give any help or a tutorial I'd be most thankful.

Ste.

---

### Post by Moobert on 2005-01-21
FreeNX or VNC allow remote destop control over the network, not transfer files. You ned to setup samba;

[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

then create a folder share

or

mount shares over the network

[http://ubuntuguide.org/#mountunmountnetworkfolder](http://ubuntuguide.org/#mountunmountnetworkfolder)

being xp nautilus maybe able to connect to the other windows shares without mounting using network:/// url. 

you will also need to create shares on your windows machine, just left click folders and the like and use the share menu. 
As for zonealarm to so you need to set your lan as a trusted zone then turn off the   firewall in this zone.

---

### Post by Ste on 2005-01-21
> **Moobert]FreeNX or VNC allow remote destop control over the network, not transfer files. You ned to setup samba said:**
> http://ubuntuguide.org/#sambaserver[/url]

then create a folder share

or

mount shares over the network

[http://ubuntuguide.org/#mountunmountnetworkfolder](http://ubuntuguide.org/#mountunmountnetworkfolder)

being xp nautilus maybe able to connect to the other windows shares without mounting using network:/// url. 

you will also need to create shares on your windows machine, just left click folders and the like and use the share menu. 
As for zonealarm to so you need to set your lan as a trusted zone then turn off the   firewall in this zone.
 Thanks for the info, gonna take me a while to get through it.

---

### Post by Ste on 2005-01-21
Got it working, thanks again for the help.

---

