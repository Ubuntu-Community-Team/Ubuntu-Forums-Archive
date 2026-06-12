---
title: "TOrrent"
date: 2009-07-09
forum: General Help
---

### Post by codered1444 on 2009-07-09
If i were to run vista in vbox would my dl speeds be up as high as they were before ubuntu or would dual booting be better

---

### Post by dhughes on 2009-07-09
My opinion is they wouldn't, even with port forwarding and bridged ethernet I'd say since Vista will be running in another application its performance (the OS) will be degraded which would affect its network and cause a performance loss.

 I don't know for sure but since it's not running natively it won't be as good as it could be as if you were using a dual boot set-up. But who knows it may only be a very small difference.

---

### Post by sdlynx on 2009-07-09
My internet speed through Win7 installed on vbox is just as fast as my speed on linux, so I think you'll be fine, or at least it'll be really close.

---

### Post by t4thfavor on 2009-07-10
Aren't some versions of Vista/XP limited to 10 TCP connections? I remember hearing something about home/busness versions were limited to 10 tcp sessions, and ultimate was like 100. So thats just not god for torrenting at all. I get really good speed under linux using Transmission, others report great speed with utorrent and wine.

---

### Post by credobyte on 2009-07-10
> **t4thfavor said:**
> Aren't some versions of Vista/XP limited to 10 TCP connections? I remember hearing something about home/busness versions were limited to 10 tcp sessions, and ultimate was like 100. So thats just not god for torrenting at all. I get really good speed under linux using Transmission, others report great speed with utorrent and wine.

You can change your TCP limit in almost every torrent client ( also in OS settings, tough, it's not that easy ) :)
On-topic: what's your current speed on Linux and Vista ? How big is the difference ?

---

### Post by sdlynx on 2009-07-10
> **t4thfavor said:**
> Aren't some versions of Vista/XP limited to 10 TCP connections? I remember hearing something about home/busness versions were limited to 10 tcp sessions, and ultimate was like 100. So thats just not god for torrenting at all. I get really good speed under linux using Transmission, others report great speed with utorrent and wine.

that is ridiculous!

---

### Post by Hominym on 2009-07-10
Windows XP was limited to 10 TCP connections for security reasons. TorrentFreak has a patch for it [here.]("http://torrentfreak.com/evid4226patch223d-enzip/")

Running Windows in a VM shouldn't affect your network speed at all, since it's still using the same hardware to connect.

---

### Post by lovinglinux on 2009-07-10
> **codered1444 said:**
> If i were to run vista in vbox would my dl speeds be up as high as they were before ubuntu or would dual booting be better

No. The speed of your download depends basically on client configuration, network bandwidth/configuration and torrent health.

If you are experiencing low download speeds is probably due to bad configuration or bad torrents.

[list][*] Which client do you use? (I recommend using [deluge](apt:deluge) [apt-get])
[*] What are your bandwidth limits? (post the result of [Speedtest.net)](http://www.speedtest.net/)
[*] What are your current torrent speeds and expected speeds?
[*] Have you properly configured the torrent client settings? (check [this thread](http://ubuntuforums.org/showpost.php?p=7506308&postcount=12) for help)
[*] Are you properly forwarding the port for incoming connections from the router to your machine? (visit [http://portforward.com](http://portforward.com))[/list]

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by codered1444 on 2009-07-10
in vista i did not have to change any configurations everything ran smoothly like the speeds were anywhere from 100 min to 250+ now they cant even reach 50 i know alot about torrents (like the seeds and uploaders and the health of them but sometimes my speeds on ktorrent start up really high but end up going way way down

---

### Post by hibliss on 2009-07-10
Speeds are dependent on peers in the swarm and your client settings, not which client you use.

What are your current speed settings? Number of connections per torrent? Total global upload speed? What is your available upload speed?

Are your ports forwarded?

I get the same speeds in Linux that I do in Windows, the fastest my line can handle both ways.

---

### Post by codered1444 on 2009-07-10
i realized something in preferences i enabled dht and peer exchange but why doesn't it let me do it in the torrent

---

### Post by hibliss on 2009-07-10
> **codered1444 said:**
> i realized something in preferences i enabled dht and peer exchange but why doesn't it let me do it in the torrent

If the private box is checked when the torrent is created, you will not be able to enable DHT or PEX.

---

### Post by codered1444 on 2009-07-10
what about unpn and nat-pmp could that be affecting it

---

### Post by hibliss on 2009-07-10
> **codered1444 said:**
> i know alot about torrents 

I assumed from that statement that you knew a bit more.

UPnP is a Microsoft technology for automatic port forwarding in your router. I asked if your port was forwarded, manual forwarding is always a good idea for bittorrent.

Not having your ports forwarded can certainly effect speeds. Ports have to be open on one end of the connection. If you are attempting to download from a peer who also does not have forwarded ports for their client, no connection will be made. Less peers generally means lower speeds (but not always depending on the available bandwidth of the peers in the swarm).

---

### Post by codered1444 on 2009-07-10
ok but in vista i changed no configurations and using bitlord i recieved a minimum of a 100 mbps

---

### Post by hibliss on 2009-07-10
> **codered1444 said:**
> ok but in vista i changed no configurations and using bitlord i recieved a minimum of a 100 mbps

100mbps huh? Do you have a fiber line coming to your house that you pay several thousand a month for, or do you live in Sweden? I assume you mean kBps.

Things are not automatic in Linux. They need to be configured for optimal speed (the same is true on some level in Windows clients).

Like a few people have mentioned, including me, speeds will vary from torrent to torrent, even with a perfectly configured client.

---

### Post by Bonzai11 on 2009-07-10
First Tcp connection limit has been dropped since vista sp1 or 2? and win7 I guess you guys just love to bash everything about windows eh?
Also speed should be no difference Unless one application is more accepted then another. Some sites/peers prefer utorrent/azureus or popular clients because other haven't been test for leaks or exploits that can be used to boost ratios.
After switching from deluge to Azuereus speeds increased significantly, but azureus also has the java overhead :/

---

### Post by codered1444 on 2009-07-10
srry about the mbps thing

---

### Post by lovinglinux on 2009-07-10
> **Bonzai11 said:**
> Some sites/peers prefer utorrent/azureus or popular clients because other haven't been test for leaks or exploits that can be used to boost ratios.
After switching from deluge to Azuereus speeds increased significantly, but azureus also has the java overhead :/

That's because some private tracker administrators don't do their jobs properly. The history with Deluge being banned is old, really old. It seems the argument for blocking Deluge was lack of documentation on the site along time ago. Since then, Deluge was re-written completely by the way.

I use Deluge since Windows and don't have any problems whatsoever. When downloading Ubuntu iso files, it usually reaches my connection limit. I don't even use DHT and PEX.

I also used Azureus/Vuze, but it so bloated and hog resources really bad due to Java. You can do a lot of stuff with it, but it has too many settings for my needs. Deluge on the other hand, is easy to configure and has everything essential for torrenting.

---

