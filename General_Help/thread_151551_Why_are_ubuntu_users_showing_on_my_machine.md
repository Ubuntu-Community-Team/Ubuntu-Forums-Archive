---
title: "Why are ubuntu users showing on my machine ?"
date: 2006-03-28
forum: General Help
---

### Post by petef on 2006-03-28
Im running Etherape 0.9.4 on my work network and every so often I see my Ubuntu machine connecting with other Ubuntu users, shows as eg: forester.ubuntu.com this one has popped up a couple of times ? 

I have firestarter, apache, mysql installed ? 

Cheers

Pete

---

### Post by petef on 2006-03-28
Anyone ?

---

### Post by TallMatthew on 2006-03-28
What TCP/UDP port?  How often?

It could be the update manager.

---

### Post by tomski on 2006-03-28
while you are runnig etherape if you have any application(gaim, firefox) that uses any of the connection devices ie: netcard, adsl modem card,etc then you will see all those connections to your machine and network.
take this example:

your router is on:192.168.1.1 /24 providing dchp to you and your brother

your pc is on:192.168.1.2 /24 also you have gaim,firefox running plus you just run apt-get update

your brothers pc is on:192.168.1.3 /24 he has just msn, & I.E running

when you run etherape you are provided with a visual representation of your network(192.168.1.0 /24) plus all external connections to that network so you will see is:
your connections =  all the servers listed in /etc/apt/sources.lst, plus servers you connected to using gaim & firefox

your brothers connections = servers he has contacted via msn & IE

you router connections = hardware lookup to both you & your brother, dhcp checks plus if it caches dns it will look up the ip for each website you & your brother look at plus each netcard will also send out a broadcast to the router telling it what its hardware address is and its current ip address this will be regular

so on the whole that is a very busy network

each colour you see is a different protocol the width of each line is the data being sent/recieved so the next time you are running etherape do a quick apt-get update and you will see a 'spiders web' of connections or if you use the personalised home page of google every time that refreshes you will see lots of connections all at once but with the same colour line


hope this helps

---

### Post by The Warlock on 2006-03-28
[QUOTE=petef]Im running Etherape 0.9.4 on my work network and every so often I see my Ubuntu machine connecting with other Ubuntu users, shows as eg: forester.ubuntu.com this one has popped up a couple of times ? 

I have firestarter, apache, mysql installed ? 

Cheers

Pete[/QUOTE]

Not sure, but I'm guessing it's the update manager.

---

### Post by towsonu2003 on 2006-03-28
you could check out the conversation with ethereal to see what's they're saying to each other. I to think it's the update manager (or time syncronization, or wheather if you have such service)

PS. Firefox can't find the server at forester.ubuntu.com

---

