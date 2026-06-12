---
title: "No torrent clients will connect to any peers."
date: 2011-06-06
forum: General Help
---

### Post by expergefacio on 2011-06-06
I've used Transmission for about a year now, and i haven't had any problems with it. But a couple of weeks ago it suddenly wouldn't connect to any peers. It gets peer list from tracker, then nothing happens.

Ive tried using different clients (Vuze and Deluge) and the same story goes for both. 

Ive tried restarting the router in case of any DNS crap, getting nothing.

Ive installed Firestarter only to create an exception for traffic on the torrent ports (even though it probably is pointless)

Now both google and myself seem to be out of ideas. Does anybody have something i could try out and possibly fix this. Everything points to some software issue...

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did you setup port fowarding within your router configuration yet?

---

### Post by expergefacio on 2011-06-06
> **linuxinstalledfromhdd said:**
> Did you setup port fowarding within your router configuration yet?

Not really relevant, if i ha it enabled that would not help the fact that i cant make outgoing connections...

---

### Post by linuxinstalledfromhdd on 2011-06-06
Sounds like to me, without port forwarding, they have caught the port and blocked it.  

You need to use port forwarding with your router, or this will always happen sooner or later.  Google for instructions on port forwarding for your make and model of router.  Until you have that set up correctly, you will never know if that is the real cause or not.  What you are attempting to do is only going to work for a while, until you set it up correctly on a dynamic IP.

---

