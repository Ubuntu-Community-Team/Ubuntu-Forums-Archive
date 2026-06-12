---
title: "what listening port for bit torrent"
date: 2009-07-25
forum: General Help
---

### Post by rastro123 on 2009-07-25
hi, I went to and internet cafe with my laptop and started messing with proxy servers. I changed it back when it didnt seem to work well, but now bit torrent has stopped downloading, saying that the listening port is closed. Can anyone please tell me what to do? I've forgotton what the port was set at in the first place now and am totally at a loss! Many thanx.

---

### Post by /\/\@/\/ |_| on 2009-07-25
The default listening ports for bittorent are 6881-6889.
where did you change your proxy settings?
It Seems you have closed these ports.
To open port 6881 use
```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT 
```
maybe this will help.
or if you are behind a firewall , that firewall may also have closed these ports..

---

### Post by rastro123 on 2009-07-25
thanks mate, Im on the case now. When I went to the cafe, I tried one of the proxies from usdaily proxies, or something like that - I wanted to send an email to someone without them knowing where  I am. 
Today Im on a piggyback of someones connection, where I normally go, - everything is fine, eccept bit torrent has stopped. the place where I changed things was in system- preferences - proxy settings. Ill try what you just suggested now. thanks again mate.

---

### Post by rastro123 on 2009-07-25
Hello again, I just tried what you suggested but it still keeps saying the port is closed. Also I tried updating the system and it failed saying it could not connect. Im getting google and everywhere else ok. Any ideas mate?

---

### Post by SlugSlug on 2009-07-25
if your piggy backing go to shields up run a test and pick an open port

---

### Post by mikewhatever on 2009-07-25
I think it is irrelevant what the listening port is, since it should be open unless: a) you closed it on purpose, b) you are behind a router/proxy. Since the first scenario is unlikely, you'll probably need access to that router/proxy configurations to make ports open.

---

### Post by rastro123 on 2009-07-25
ok, thanks guys, Im gonna go back to an internet cafe just now and see if that solves things, Im wondering if I've been rumbled for getting this guys connection here. It seems strange to me. -oh, what is shields up pls?

---

### Post by SlugSlug on 2009-07-25
sheilds up will show you what ports are open on that guys router but thinking about it he would not forwqard ports to you LAN IP, so maybe you just turned upnp off... ??

---

### Post by rastro123 on 2009-07-25
Just to say thanks again for all replies. I came to an internet cafe, and bingo, everything has gone back to normal, so I guess the guy has noticed his connection slowing down in the middle of the night and changed things on his router.

---

### Post by mikewhatever on 2009-07-25
> **rastro123 said:**
> Just to say thanks again for all replies. I came to an internet cafe, and bingo, everything has gone back to normal, so I guess the guy has noticed his connection slowing down in the middle of the night and changed things on his router.

What guy, your neighbor? You really shouldn't be using bittorrent in a cafe, nor should you connect to other peoples' networks. It's illegal, and helping you with such activities is against the forums' rules.

---

### Post by hibliss on 2009-07-25
What exactly do you mean piggybacking? Stealing wifi?

If it is your connection (or you know this person), the port needs to be opened in the router as stated above. This is easy to do and the best solution. You may have previously been depending on UPnP.

Do not use the standard Bittorrent ports, pick a higher non standard port as many users and trackers block the standard ports from the original bittorrent client.

What bittorrent client are you using? Even if your ports are not open, you can generally still connect to some users in a swarm. A port only has to be open on one side of a connection. 

Many coffee shops and public wifi access points block bittorrent, and for good reason. These are places to check email and are meant for light use of the connection for work or browsing, not heavy use as a server (which is what you are when you run bittorrent).

---

### Post by rastro123 on 2009-07-26
and why should I not use bit torrent in a cafe????

---

