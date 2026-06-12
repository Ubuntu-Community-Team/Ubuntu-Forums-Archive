---
title: "Amule"
date: 2005-02-26
forum: General Help
---

### Post by benbert on 2005-02-26
Greetings,

I see there are already a lot of threads about Amule but I read them all and none of them helped. I have just recently switched from Gentoo Linux on which I had Amule running perfectly. Now for whatever reason when I run it on Ubuntu it says I have a lowID and hardly ever connects, not even when left open for hours. The few times I do find a connection, things begin to get uploaded but nothing ever downloads. I already have all the ports forwarded that are mentioned on the Amule site and tried forwarding more that people have mentioned in various threads but I don’t seem to have any luck, any suggestions would be greatly appreciated.

---

### Post by bored2k on 2005-02-26
[QUOTE=benbert]Greetings,

I see there are already a lot of threads about Amule but I read them all and none of them helped. I have just recently switched from Gentoo Linux on which I had Amule running perfectly. Now for whatever reason when I run it on Ubuntu it says I have a lowID and hardly ever connects, not even when left open for hours. The few times I do find a connection, things begin to get uploaded but nothing ever downloads. I already have all the ports forwarded that are mentioned on the Amule site and tried forwarding more that people have mentioned in various threads but I don’t seem to have any luck, any suggestions would be greatly appreciated.[/QUOTE]

1 First of all install amule-utils , it has some good config utilities.

U can forget what amule site or people say , open ur adv. configuration and get info on wich ports it wants to use [UDP/TCP] .

2 I know theres no need to say u need to specify to ur router ur forwarding tcp or udp ports...

3 If its still low id , supposedly ports are blocked, to test this go to

[PC Flank](http://www.pcflank.com)  or [DSL Reports](http://www.dslreports.com) 

and do an advanced -specific- port scan , if ur forwarded correctly, ur ports should appear open, if not ... u are to deal with ur router 
Info here -- > [Port Forwarding Help](http://www.portforward.com/) 


In the mean time, u can try other good P2P like Nicotine [based on Soulseek] or [Limewire Free](http://www.limewire.org)  [java needed for LWire, check ubuntu wiki for installing Java

---

### Post by benbert on 2005-02-26
[QUOTE=bored2k]1 First of all install amule-utils , it has some good config utilities.

U can forget what amule site or people say , open ur adv. configuration and get info on wich ports it wants to use [UDP/TCP] .

2 I know theres no need to say u need to specify to ur router ur forwarding tcp or udp ports...

3 If its still low id , supposedly ports are blocked, to test this go to

[PC Flank](http://www.pcflank.com)  or [DSL Reports](http://www.dslreports.com) 

and do an advanced -specific- port scan , if ur forwarded correctly, ur ports should appear open, if not ... u are to deal with ur router 
Info here -- > [Port Forwarding Help](http://www.portforward.com/) [/QUOTE]

I looked at my router settings and everything looks ok, i also looked at the port forwarding help page you linked to and everything is set up the way that shows. When i tried to use PC Flank it gives me the message:

```
The test has found that the IP address used by your computer cannot be scanned. This commonly occurs because of a firewall program on your computer and/or you are connected to the Internet through a proxy-server or your ISP uses Network Address Translation (NAT) to share IP addresses. 

This means the test cannot check your system as the results of the testing would be incorrect.  
``` 

When i try with dslreports.com it tells me both TCP and UPD are all filtered. Although when i scan my mac which is connected through the same router it finds open ports. The ports that Amule is set to use are set to forward to the correct IP, just the port scanner thinks not.

Thanks.

---

### Post by benbert on 2005-02-26
I also noticed i seem to be getting two messages continually coming up in the Server Info tab. The first says "zlib must be used not only advertized" and the second "your IP is currently blacklisted". I realise what the second one means, but can anyone tell me how long it is before you get un-blacklisted and i have no idea what the first message means.

---

### Post by SickBoy on 2005-02-27
That message happens when you send your list of shares uncompressed to the server.

Update to amule 2 to solve the problem ;)

Almost forgot: package is here: [http://forum.amule.org/thread.php?sid=44db1bcbd0dbc96cb67dc1a673bb9b8b&postid=21131#post21131](http://forum.amule.org/thread.php?sid=44db1bcbd0dbc96cb67dc1a673bb9b8b&postid=21131#post21131)

---

### Post by benbert on 2005-02-27
Thankyou so much, that's fixed everything right up. It's running better then it ever has now too. I'm not too keen on the new search page, not having the choice to search videos, music etc. But that is only a minor problem. Thanks again.

---

### Post by ThePainter on 2005-02-27
Hi,
Yeah I got that warning in Amule and Emule back in XP and I corrected it by opening the ports in my firewall.
I also got more sources and faster downloads by doing this in Overnet and KLite in XP.
I only use A mule in Linux.

---

### Post by bored2k on 2005-02-27
> **SickBoy]That message happens when you send your list of shares uncompressed to the server.

Update to amule 2 to solve the problem  said:**
> http://forum.amule.org/thread.php?sid=44db1bcbd0dbc96cb67dc1a673bb9b8b&postid=21131#post21131[/url]


"gracias" a lot for that aMULE 2 L!nk 8-)

---

