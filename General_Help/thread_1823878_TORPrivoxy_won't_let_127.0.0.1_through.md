---
title: "TOR/Privoxy won't let 127.0.0.1 through"
date: 2011-08-12
forum: General Help
---

### Post by spradlig on 2011-08-12
I've been running Ubuntu 9.04 for a while now with TOR/Privoxy working for outside sites.  However, I've never been able to see other computers on my LAN (I have several servers running).

I have several PHP programs which I call via curl as a cron job.  in 9.04 it never seemed to be a problem to call curl [http://127.0.0.1/...php](http://127.0.0.1/...php).  However, since 9.04 is no longer supported I moved to 10.04 and now some of these crons don't seem to be running.

If I use Firefox to get to my PHP scripts via the IP address or 127.0.0.1 it usually works fine.  When I use curl from the command line it does not.  When I use Firefox to check my IP it shows a TOR IP not mine so I assume the Firefox is using TOR/Privoxy just like curl is.  And I can use curl from the command to get WWW addresses.  When I use "curl http://icanhazip.com" I get a TOR IP returned not my own.

So in genenral TOR and Privoxy are working but I have never been able to get Privoxy to let me curl 127.0.0.1 or localhost or the server's LAN IP.  And even Firefox can't see the other servers on my LAN.

The Privoxy log states:
"Crunch: Forwarding failed: http://127.0.0.1/"

I'm hoping that's more useful to someone out there than it is to me.  That seems to be a pretty worthless message to me.

All of these lines are uncommented in the Privoxy config:
        forward         192.168.*.*/     .  
        forward         10.*.*.*/        .  
        forward         127.*.*.*/       .
And this is how I get Privoxy to work with TOR:
# TOR
forward-socks4a / localhost:9050 .

The config line in Privoxy default config is:
#        forward-socks5   /               127.0.0.1:9050 .
but I don't think I've ever gotten that line to work properly.

The $HOME/.bashrc is setup correctly to send all curl requests to TOR/Privoxy through port 8118.  I even use one of these servers as a proxy for one of my Windows boxes.  But I can't get Privoxy to let me call 127.0.0.1.

Please Help!?!?!

---

