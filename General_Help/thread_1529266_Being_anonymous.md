---
title: "Being anonymous?"
date: 2010-07-12
forum: General Help
---

### Post by GrantStoner on 2010-07-12
How would I go about achieving total anonymity on my laptop on Ubuntu? How would I go about permanently changing (or just hiding) my IP address for my laptop, as well as my MAC address? And is there any other possible way for anyone to identify my laptop? From what I understand, there's only a gateway IP (from the router), the IP assigned to my laptop, and my MAC address. Is there anything else? Oh, and one last question: is there a separate IP for the wireless card that my laptop came with, or is that just the IP for my laptop?

I don't want to simply block certain IPs from accessing my laptop. I've used many IP blockers before. I don't want to block access to my laptop, I want to make it seem as though it doesn't exist. My laptop is shy and it doesn't want to be found. ;)

Thanks in advance.

---

### Post by sxmaxchine on 2010-07-12
I dont know if it is possible to become completely hiden.

Im not possitive but im pretty sure you need to send your information to web servers so it knows to send back some information to your laptop.

---

### Post by Yarui on 2010-07-12
What exactly do you want to stay hidden from?  Somewhere someone will always see where you are coming from.  If you want to stay hidden from everything you are kind of out of luck.  If you don't mind just a few servers seeing your laptop, though, you can use a proxy.

Proxies are servers you connect to that then connect to your destination servers, so that those servers just see the proxy server.  The proxy server then sends the information back to you.  Basically this means your activity is "seen" just by your ISP and the proxy server.

If the proxy communicates with you through an encrypted connection then the ISP won't be capable of viewing anything you are doing (if you are paranoid enough to think they are looking).  This means the ISP can see that you are doing something, they just can't see what, and that means that the proxy server is the only server that can really see your activity.  If you are using a trustworthy proxy server then you can rest assured that no one is seeing what you are doing, but the proxy server is capable of seeing pretty much everything you do, except encrypted date, if the people operating it choose to do so.

---

### Post by GrantStoner on 2010-07-12
Well, if I changed my IP for my laptop and my MAC address, the only way of locating me would be through the gateway IP from the router right? That's ok If I'm in a public place, but not for home. I know how to temporarily change my IP and MAC, but it always resets to the normal when i reboot. And proxies are for browsing right? What would protect other things like IMs or other tools I use that access the internet?

---

### Post by betrunkenaffe on 2010-07-12
Either I don't understand your goals and you are talking about doing something other than what I think you are talking about or you haven't tried the whole change IP thing because it shouldn't work at all...

[http://computer.howstuffworks.com/internet/basics/question549.htm]("http://computer.howstuffworks.com/internet/basics/question549.htm")

Proxy servers would be the best you'll get for being 100% anonymous UNLESS you are unconcerned with reply packets. Best suggestions would be to disable 3rd party cookies, avoid using your real name in username/computer name. Move around to unsecured wireless networks is also very good since then you are piggybacking other people's connections.

Overall, you won't be able to stay completely invisible since there's always a traceback.

---

### Post by lordskid on 2010-07-12
piggybacks are illegal in some countries. like singapore. but mostly people don't care. firewalls can help in anonymity too. by blocking ports that are unused. with what I understand you are trying to do, the best is to use a proxy. changing your ip address means your ISP still knows what your up to. with encrypted proxies only the proxy server knows.

---

### Post by GrantStoner on 2010-07-12
I'm not talking "locating me" like seeing my geographical location at the moment i'm on the web. Hypothetical situation *ahem*: I'm on my laptop at the local junior college and I'm playing (and I use that term loosely) with metasploit. Wouldn't they or their ISP be able to say "hey IP address blah blah blah was doing very bad things here!" and record my IP and MAC addresses? 

Or hypothetical situation #2: I'm downloading a torrent (for non-free software) then my ISP can say that my computer with the IP and MAC address of blah blah blah was downloading illegal softwares. Right? Unless those are both changed right? Then they can only say that someone using my router did it, but not necessarily that it was me.

---

### Post by giddyup306 on 2010-07-12
If you're worried about them seeing your IP just change it in Firefox.  Edit > preferences > advanced > settings then click on manually manually configure proxy and type in whatever IP you want.  The only thing is that most of the free proxys aren't SSL and a lot of the time they are illegal because someone hacked into a weak server.  Plus if you connect to one, it may dissappear in seconds. If you want to hide your IP because of illegal things... well that's up to your morals.  I got really concerned about security when I caught the Ford Motor Company monitoring my computer.  I used to work for corporate, and I think they were worried that I was giving away trade secrets or something.  I did a reverse IP search and even have the suite number where it came from.  I was so angry over the deal that I wrote a letter (which I'm debating if I want to send or not).  



> **lordskid said:**
> piggybacks are illegal in some countries. like singapore. but mostly people don't care. firewalls can help in anonymity too. by blocking ports that are unused. with what I understand you are trying to do, the best is to use a proxy. changing your ip address means your ISP still knows what your up to. with encrypted proxies only the proxy server knows.
From what I understand, Linux doesn't open ports like Windows does.  There is a firewall called Firestarter and an IP Blocker called Mobloque.  I have both on my computers.

---

### Post by lisati on 2010-07-12
Firestarter isn't a firewall, it's a frontend to a firewall that is depecrated. ufw and gufw are popular alternatives these days.

It's possible to learn *something* about you when you're online, but proxies can go some way to help with anonymity. Have a look here: [http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami)

And don't forget to keep things "above board" if you're connecting through someone else's network.

---

### Post by smellyman on 2010-07-12
could try TOR, but speed may be an issue.

---

### Post by Bradtek on 2010-07-12
[http://www.torproject.org/](http://www.torproject.org/)

---

### Post by giddyup306 on 2010-07-12
> **Bradtek said:**
> [http://www.torproject.org/](http://www.torproject.org/)
Some of the packages are missing. :(  While I was trying to find an alternate, I found a Torbutton plugin for Firefox tho...

---

### Post by t0p on 2010-07-12
For proxy services to "hide" my IP address, I like [Your Freedom]("http://your-freedom.net") and [ibvpn]("http://ibvpn").  Your Freedom is pretty slow.  Ibvpn is pretty fast, but you got to pay.

If you want to *spoof* a MAC address (you can't *change* a MAC address, its hardwired into your equipment) there's a little app called Macchanger.  Yeah, yeah, I didn't name the thing.

---

### Post by betrunkenaffe on 2010-07-12
Just want to point out that Mac spoofing won't do anything unless you change your mac daily/hourly. All the MAC will provide is a verification of the machine which was being utilized, spoofing it will still be visible to anyone that checks your computer (thereby still giving the verification).

Any and all traffic can be monitored by an external source. Every link along the path through the internet that your communications travel could log it (or details about it). Encryption will prevent someone from being able to read the data but the source/destination will always be available.

---

