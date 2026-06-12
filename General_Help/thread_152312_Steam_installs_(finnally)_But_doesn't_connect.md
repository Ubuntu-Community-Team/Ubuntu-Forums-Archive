---
title: "Steam installs (finnally) But doesn't connect"
date: 2006-03-29
forum: General Help
---

### Post by balrog900 on 2006-03-29
Steam installs but then cannot connect. I'm using wine. BUT I've also noticed the same issue with all bit-torrent clients on here as well. What could be affecting this?
I would love to find a solution to this one i've been searching the net for quite some time.

---

### Post by jbennett on 2006-03-29
[QUOTE=balrog900]Steam installs but then cannot connect. I'm using wine. BUT I've also noticed the same issue with all bit-torrent clients on here as well. What could be affecting this?
I would love to find a solution to this one i've been searching the net for quite some time.[/QUOTE]

I don't have a lot of experience using BitTorrent but let me take a stab at it.  Are you accessing the internet through a router or firewall?  If that's the case then you may need to configure the router to allow port forwarding through a specified port, and then configure Steam to use that port.

Hope that helps.  Be sure to post your results.

---

### Post by balrog900 on 2006-03-29
Unfortunately.....no router. No firewall either, (unless theres one on this motherboard than i'm unaware of but i doubt it this mobo is pretty old). I'm on a university campus but steam works fine on xp etc etc etc.

---

### Post by balrog900 on 2006-03-29
I've been thinking, does ubuntu come with any sort of "security system" like fedora core does? Becausei remember when i did this on fedora i have to change some security things. However If they exist I don't think they are in the same place.

---

### Post by siminone on 2006-03-29
I think jbennett is correct and you will need to install the firewall program Firestarter.

You will have to set up a policy to allow inbound connection. You will have to check forums for Steam (I presume you are talking about steam system that half-life uses) for what port to use. 

Be very careful as you could be opening up your system to attack.

---

### Post by jbennett on 2006-03-30
Actually, I was just referring to a hardware firewall (which is essentially what a router acts as).  If Steam is just a bittorrent client then you shouldn't need to enable Firestarter because you should only need a firewall if you have anything facing outward (unless of course you were using your box as a server for bittorrent downloads by other people).  Enabling Firestarter won't make any difference to whether or not Steam works properly; as far as that goes, I'm stumped.

Hope this helped, if I'm mistaken on any of these points someone please feel free to correct me.

---

