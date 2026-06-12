---
title: "how do i download torrents in ubuntu?"
date: 2010-02-05
forum: General Help
---

### Post by aviramof on 2010-02-05
i'm downloading the files but it doesn't start to download.

---

### Post by howefield on 2010-02-05
Are you using the included bittorrent client, Transmission ?

---

### Post by linden940 on 2010-02-05
download the torrent file and push open..it should open the client an start the download

---

### Post by Cabs21 on 2010-02-05
personally I use uTorrent thru wine for the private torrent site and deluge for public torrents.  Some reason the private site does not support deluge.

---

### Post by dbowlin17 on 2010-02-05
I use transmission. After you download the .torrent file, then just click on it to open. it should open in transmission and provide you with the files that can be downloaded. you then can click ok. For me, as i have used both bittorrent and transmission, transmission is a bit slower to start off. also, if you have no download limits then you should change how many peers you can connect to, its pretty nice when you are downloading from 200+ people. lots of times i have to right click on the torrent inside transmission and say ask tracker for more peers to get it started but thats it. hope that helps.

---

### Post by linden940 on 2010-02-05
> **dbowlin17 said:**
> I use transmission. After you download the .torrent file, then just click on it to open. it should open in transmission and provide you with the files that can be downloaded. you then can click ok. For me, as i have used both bittorrent and transmission, transmission is a bit slower to start off. also, if you have no download limits then you should change how many peers you can connect to, its pretty nice when you are downloading from 200+ people. lots of times i have to right click on the torrent inside transmission and say ask tracker for more peers to get it started but thats it. hope that helps.

never had that problem with transmission...i download it and it just works...or for me it dos

---

### Post by aviramof on 2010-02-05
transmision said port is close why is that and what port do you recommend.
is there a firewall i need to disable?

---

### Post by Cabs21 on 2010-02-05
your port is closed on your router to protect your network from intruders.  I recommend HIGH ports.  I use some port above 64000 (dont remember exact number) and I forward all info for uTorrent through that port.

---

### Post by howefield on 2010-02-05
> **aviramof said:**
> transmision said port is close why is that and what port do you recommend.
is there a firewall i need to disable?

Open the port on your router (TCP/51413 to your ubuntu PC is the default port.)

[http://trac.transmissionbt.com/wiki/PortForwardingGuide](http://trac.transmissionbt.com/wiki/PortForwardingGuide)

---

### Post by mk1w86 on 2010-02-05
You can test if the correct ports are open from Transmission by going to:

Edit >> Preferences >> Network tab

---

### Post by Charlietje on 2010-02-05
rtorrent

Is commandline and a very fast torrent.
Once used to work with it, very easy

---

### Post by aviramof on 2010-02-05
i don't have a router is plain adsl modem connect to realtek network card i don't use routers if i need home network i have another onboard network card and a reverse RG45 cable and i'm using ics or ipv6 and etc which remind me that i need to check how to 
install ipv6 or teredo in this os as for netwrok option i'm fully aware of this that is why
i said the software said the port is close but it seem to be that i am able to download in
the end and in full speed of 500KB which is my max but i would still like to fix this problem
and not install utorrent and etc via wine or some other bittorent software transmission is 
just fine for me the question is does it's a problem with the firewall and how can i check it.

thanks in advance.

---

