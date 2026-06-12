---
title: "anybody help old laptop want to turn ito a server running a torrent app"
date: 2010-05-31
forum: General Help
---

### Post by shaunandej on 2010-05-31
ok i have mybook nas but dont want to hack it a main laptop dell fairly new dual boting windows and linux mint and ubuntu and a advent 7098 laptop with no screen in the attic running mint at the moment basicly i want to to the laptop in the attic into a server that just runs a torrent app that i can access from my main laptop to add torrents and have it save torrents to my nas any ideas

---

### Post by rizzeh on 2010-05-31
look into rtorrent - CL based torrent client can be controlled either by SSH or web server. I have one set up with rtorrent getting jobs from a watched folder. Coupled with screen command it is very handy indeed.
[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide")

---

### Post by shaunandej on 2010-05-31
i was looking at transmission as its very similar to waht i was used to i can get everything working if i install ubuntu first or mint but i want a basic install then just transmission and nothing else is that possable

---

### Post by nothingspecial on 2010-05-31
+1 for rtorrent.

If you run with screen, you can control your torrents from anywhere in the world.

There is a good set up guide [[COLOR="Magenta"]here[/COLOR]]("http://wiki.archlinux.org/index.php/RTorrent") 

So now you just need a ubuntu server (or minimal) install. openssh-server, openssh-client, rtorrent and screen (or byobu which is a pimped up ubuntu screen).


When setting everything up, I found, installing ncurses-base and wicd alot easier for configuring my network, allthough editing the network config files is well documented.

If all you want to do is torrent then installing a full gui is pointless.

However do what you will, just my opinion. :)

---

### Post by shaunandej on 2010-05-31
thanks will go through the processes of getting set up can you confirm that i will be able to save files externaly to my networked nas

---

### Post by nothingspecial on 2010-05-31
Have a look at [[COLOR="Magenta"]sshfs[/COLOR]]("https://help.ubuntu.com/community/SSHFS")

---

### Post by prshah on 2010-05-31
> **shaunandej said:**
> thanks will go through the processes of getting set up can you confirm that i will be able to save files externaly to my networked nas

Yes, you can; rtorrent has an option to "move" completed torrents to another location (in this case your NAS).

It is not a good idea to move in-progress torrent downloads to an external drive (though you CAN do it).

---

### Post by sdennie on 2010-05-31
I use transmission-daemon to do what you are describing.  You only need a minimal install of Ubuntu to set it up and, it too allows for an incomplete and complete location.  It also has an awesome web interface that you can either expose to the outside world and control it from any device or hide behind a firewall and ssh tunnel into it.

I've used rtorrent in the past as well and the biggest headache is going to be getting the configuration setup properly regardless of which you decide on.  Have a look at both and see which you think you might prefer.

---

