---
title: "How to port forward 25565 with 2WIRE router"
date: 2011-10-19
forum: General Help
---

### Post by felinoel on 2011-10-19
I've followed tons of guides but my port is still seemingly closed, there are programs out there that will do it for you but they are Windows only...

Any help?

---

### Post by felinoel on 2011-10-20
I spoke with my ISP and after thirty minutes of explaining what I was trying to do they said they didn't know how to help and that they would transfer me to people who did, and when I got transferred I got hung up on...

---

### Post by felinoel on 2011-10-20
Followed tons of guides that didn't help... anyone?

---

### Post by Snowboi on 2011-10-20
> **felinoel said:**
> Followed tons of guides that didn't help... anyone?

It depends on the router
but for the most part 

on google type "ip"
take your ip copy and paste it into your address bar
from there you need to know your id and password to access your router configuration
if you do NOT know it then contact your ISP and ask them for those credentials

i believe it then is firewall -> firewall settings and you can add a per-defined port

the port tells me this is a minecraft server ;P
[http://portforward.com/english/routers/port_forwarding/2wire/1701HG/Minecraft_Server.htm](http://portforward.com/english/routers/port_forwarding/2wire/1701HG/Minecraft_Server.htm)
send me the ip when your done ^_^

---

### Post by felinoel on 2011-10-20
> **Snowboi said:**
> It depends on the router
but for the most part 

on google type "ip"
take your ip copy and paste it into your address bar
from there you need to know your id and password to access your router configuration
if you do NOT know it then contact your ISP and ask them for those credentials

i believe it then is firewall -> firewall settings and you can add a per-defined port

the port tells me this is a minecraft server ;P
[http://portforward.com/english/routers/port_forwarding/2wire/1701HG/Minecraft_Server.htm](http://portforward.com/english/routers/port_forwarding/2wire/1701HG/Minecraft_Server.htm)
send me the ip when your done ^_^

Tons of guides told me to do all that, it is a 2WIRE router, here are some screenshots that were requested by some people on another message board who I guess gave up...

[img]http://i46.photobucket.com/albums/f130/felinoel/Screenshot-6.png[/img]
[img]http://i46.photobucket.com/albums/f130/felinoel/Screenshot-5.png[/img]
[img]http://i46.photobucket.com/albums/f130/felinoel/Screenshot-9.png[/img]
[img]http://i46.photobucket.com/albums/f130/felinoel/Screenshot-11.png[/img]
[img]http://i46.photobucket.com/albums/f130/felinoel/Screenshot-8.png[/img]

---

### Post by Snowboi on 2011-10-20
I don't understand what the problem is then...

If your port seems closed try this

Entering localhost (no spaces) into direct connection

if it won't connect it might have to do with the ubuntu firewall ...
not likely thought.

remember you ALWAYS have to be running the server so make sure minecraft_server.jar is always open even when you start minecraft and connect to your server (never turn it off until you wanna shutdown the server using /stop)

basically i mean open mincraft_server.jar leave it running then open up minecraft and connect to it
it should work then for other players

if not why not try hamachi ?
it works for linux as a beta

[https://secure.logmein.com/labs/](https://secure.logmein.com/labs/)

just set up a server through hamachi no need to port forward, just make sure you and everyone who wants to play has hamachi

(make sure the people who wanna connect are white listed or just turn off white listing)

---

### Post by felinoel on 2011-10-20
> **Snowboi said:**
> I don't understand what the problem is then...

If your port seems closed try thisPeople can't connect and it says it times out in the canyouseeme.org site

> Entering localhost (no spaces) into direct connectionRight... could you elaborate a little more? <.<;

> if it won't connect it might have to do with the ubuntu firewall ...
not likely thought.A lot of people using Ubuntu do seem to have this issue according to the comments on an Ubuntu Minecraft server guide on Youtube...

> remember you ALWAYS have to be running the server so make sure minecraft_server.jar is always open even when you start minecraft and connect to your server (never turn it off until you wanna shutdown the server using /stop)It is running and when I do turn it off I use the stop command

> basically i mean open mincraft_server.jar leave it running then open up minecraft and connect to it
it should work then for other playersTwo different people have tried and could not

> if not why not try hamachi ?
it works for linux as a beta

[https://secure.logmein.com/labs/](https://secure.logmein.com/labs/)I hate hamachi, especially its GUI-less linux version...

> just set up a server through hamachi no need to port forward, just make sure you and everyone who wants to play has hamachiYou are sure this is the only route? x.x

> (make sure the people who wanna connect are white listed or just turn off white listing)They are white listed.

---

### Post by Snowboi on 2011-10-20
1) try to port forward using the UDP instead of TCP this time

if that does not work

2) 
```
sudo iptables -A INPUT -p tcp --dport 25565 -j ACCEPT
```then

```
/etc/init.d/iptables save
```

and finally

```
/etc/init.d/iptables restart
```

3) Try the above using udp instead of tcp

and by localhost i meant
turn on minecraft login > multiplayer > direct connection and type in localhost and try logging in (but thats not necessarily since you can login to your own server)

just to be safe afterwards close all unneeded ports
using
```
iptables -A INPUT -p tcp --dport 25 -j DROP
```

then save it and restart it

```
/etc/init.d/iptables save
```
then
```
/etc/init.d/iptables restart
```

---

### Post by felinoel on 2011-10-20
> **Snowboi said:**
> 1) try to port forward using the UDP instead of TCP this time


Same info?

---

### Post by felinoel on 2011-10-20
> **felinoel said:**
> Same info?

I went ahead and did it as the same info and HEY!?!?! IT IS WORKING NOW FINALLY?!?!?!!!!!!!!!!!!!

I am going to go take a couple aspirins for the headache this has caused and then let my players know it works, thanks and you are quite awesome.

I considered switching to UDP but mentioned it in another forum with these guys and they ignored the thought completely so I figured it was a dumb idea...

---

### Post by Snowboi on 2011-10-20
> **felinoel said:**
> I went ahead and did it as the same info and HEY!?!?! IT IS WORKING NOW FINALLY?!?!?!!!!!!!!!!!!!

I am going to go take a couple aspirins for the headache this has caused and then let my players know it works, thanks and you are quite awesome.

I considered switching to UDP but mentioned it in another forum with these guys and they ignored the thought completely so I figured it was a dumb idea...

Enjoy your server :D
be sure to mark the thread as solved :D

---

