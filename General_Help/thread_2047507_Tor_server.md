---
title: "Tor server"
date: 2012-08-25
forum: General Help
---

### Post by goodvikings on 2012-08-25
Hiya all

Has anyone got a tor server up and running before? I'm having some issues with it.

I'm trying to get Tor running on ubuntu 10.04 server, the idea being to get my local machines to connect to that server instead of configuring tor on every machine. Unfortunately, I can't find a decent guide that is actually in date.

It seems to be working judging by log files, but my end machines aren't working when connecting to the server - So I can't really tell if it's a problem on the client side or the server side. I would imagine its server side purely because client side is so simple to set up: point the browser at the socks proxy on address:port.

Tor config, and showing the port 9050 is being listened on.

```

[BLANK LINES TRIMMED]
root@server:/var/log/tor# grep -v ^# < /etc/tor/torrc
SocksPort 9050 # Default: Bind to localhost:9050 for local connections.
SocksPolicy accept *
RunAsDaemon 1
DataDirectory /var/lib/tor
ORPort 9001
Nickname ramo
ContactInfo ramo
DirPort 9030 # what port to advertise for directory connections
ExitPolicy accept *:*
root@server:/var/log/tor# ss -aln | grep 9050
0      0                      127.0.0.1:9050                          *:*

```

Any help would be appreciated.

Cheers

---

### Post by beboylips on 2012-08-25
You need to set-up the server as a middle-man (relay) and not as an exit.

---

### Post by goodvikings on 2012-08-25
I'm trying to set it up as both...

What's missing to make it a relay? I can't see anything obvious in the config filem I thought it would just be the 

```
SocksPort 9050
ORPort 9001
```

to advertise that it was a relay, and the port to listen on for relaying.

Cheers

---

### Post by Lars Noodén on 2012-08-25
You might try using the GUI, Vidalia, to set up the configuration you want.  You can then go look at the configuration manually to see what was changed.  Vidalia is one of the few instance I find where the GUI is useful.

---

### Post by goodvikings on 2012-08-25
Yeah I tried that didn't help.

I did get it in the end though: I needed to add in SocketListenAddress 0.0.0.0 to get it to take connections from boxes other than the one the server runs on.

Thanks for the help though!

Cheers

---

