---
title: "Flummoxed by WiFi"
date: 2006-02-15
forum: General Help
---

### Post by BlacKoffee on 2006-02-15
I'm still trying to get my ubuntu to work on my WiFi net work. I've done everything everyone has told me to do, but I still can't access the net. My computer is reading the card, but it's reading it as an Unknown WiFi device. It's a Belkin F5D7000 v 0005. I can't seem to find a driver that will install right (I've used all the possible drivers at ndiswrapper's wiki list), but it's been connecting to the network with out the proper driver as an Atheos or atheros? Whichever the brand is. I can access all of the computers on my network, and I can transfer files and such, but it doesn't find any internet connection. I've used the gtkwifi thing to connect, I've connected manually via the administrator option, I've tried it with WEP on and WEP off. But still no network. 

I'm not sure what I need to type to ping google. A friend of mine was supposed to help me set all this up, but he's dissappeared from the face of the earth. (Argh). 

Oh, and here's the other wierd thing... Everytime I try to get my WiFi to work, all the other computers on the network lose their internet connection. The network I'm on is using a Microsuck router. Could that be the problem?

PLEASE HELP! :cry:

---

### Post by BlacKoffee on 2006-02-15
Please? Can someone help me? I love ubuntu, but if I can't get this working, I'll have to go back to windows (BLEH)

---

### Post by LoathRevolver on 2006-02-15
WiFi is the one thing that pisses me off the most about the whole Linux experience. I've never been able to get it working reliably. Do this, do that, try this, try that... Everyone is full of info (which is awesome), but it's still frustrating. I wish I could help you out, but I've got my own problems. I feel your pain. ;)

---

### Post by nanotube on 2006-02-15
hey
if you can access computers on your local network, and transfer files, that means your wireless is getting an ip and working properly.
so my guess as to whats wrong is your dns resolution (ie, translating google.com to its IP address). 
to ping, open up a terminal (applications>accessories>terminal) and type 
```
ping google.com
```
if that does not work, then try 
```
ping 216.239.37.104
```
(this pings directly by ip address). 
if you get no reply from google.com, but get a reply from the ip address, then you know that its a dns problem, and at least can start working in the right direction to fix it. :)

---

### Post by BlacKoffee on 2006-02-19
I've pinged both, and I still can't pick up anything. And the internet still goes down for all of my other computers everytime I try to use my linux comp :S

Any other ideas?

---

### Post by xlulux on 2006-02-19
it is completely possible that you are getting no dns server ip address from your router.


you might want to try to assign the dns server ip address manually, to do this look at your routers wan status page and copy the dns server's ip address to your config in linux

then do 
ifdown ath0 (or whatever your interface is)
ifup ath0
ifconfig
ping [www.google.com](www.google.com)

---

### Post by BlacKoffee on 2006-02-19
This is going to sound stupid, but where do I find my routers wan status page? 

Do you think this could have anything to do with the fact that my router is a microsuck router? I want a new one but my mom is refusing to upgrade to a Belkin or linksys :P

Koffee

---

### Post by Plank117 on 2006-02-19
I'd just like to say that "flummoxed" is a really great word.

---

### Post by BlacKoffee on 2006-02-19
LoL. Thanks, plank :D A friend of mine used it the other day and I thought it captured my cunudrum perfectly lol. You can keep that one too ;)

Aaron

---

### Post by BlacKoffee on 2006-02-19
So no one has any ideas of what to do? Please guys, I need help!

---

### Post by Plank117 on 2006-02-20
I don't think its a Linux problem, honestly. I think your router is the root of all this IT evil. If you can connect to other computers on your network, then your card's probably working fine. You mentioned checking the status page of your router - I think that's a step in the right direction. If you know your router's IP, you can get to the status page by typing that into your browser, usually.

---

### Post by BlacKoffee on 2006-02-20
Honestly, I agree with you. Guess I'll just have to run from there :)

Thanks
Aaron

---

### Post by bmathis on 2006-02-20
[QUOTE=BlacKoffee]
Oh, and here's the other wierd thing... Everytime I try to get my WiFi to work, all the other computers on the network lose their internet connection. The network I'm on is using a Microsuck router. Could that be the problem?[/QUOTE]

If all of your computers on the network are no longer able to reach the internet after you connect your Ubuntu box, then you might have an IP conflict with the router or default gateway (which is more than likely the same as the router IP). Try manually configuring your IP address to one that you know is not being used on your network. For instance, your router/default gateway will more than likely be something like 192.168.1.1 and will start distributing DHCP at 192.168.1.100. 

Let us know if this is any help!

---

### Post by BlacKoffee on 2006-02-20
My Ubuntu computer is coming up 192.168.2.22, my laptop comes up at 192.168.2.23, and the base station desktop comes up as 192.168.2.36, so it shouldn't be an IP problem... right? 

I've heard that having mixed manufaturers for your routers and your adapters can cause problems. I've got all Belkin wireless g adapters and a Microsoft router (which I think is 802.11b instead of g). Could that be causing any problems?

Aaron

---

### Post by bmathis on 2006-02-20
the mixing of manufactures would not have anything to do with that as all the equipment do the same thing. Thats just a myth that people began using because they couldnt get their windows machine working with a wireless adaptor (cause they're that retarted... lol). Im going to try out a couple of progs for wireless and will post back my results either later today or tomorrow. Hopefully i can help you out here!


also, g adapters are backwards compatible with b by default

---

### Post by BlacKoffee on 2006-02-20
I appreciate all your help bmathis! Thanks so much!

Aaron

---

### Post by BlacKoffee on 2006-02-22
Okay, so I went and bought another router, this one Wireless G, hoping that having a universal wireless type all around might help the situation. Hey, I'm grasping at straws here.

I know that I'm connected. When I bring up the Connection Properties it says I have an 85% or higher signal strength, and that 286 packages have been recieved, 97 sent. But it still won't find the internet, and my other computers still lose their internet connection as soon as I activate my wireless card. SO WIERD :P But I can't help but shake the feeling that I'm so close I can almost taste it o_O

Help?
Aaron

---

### Post by RobinG on 2006-02-22
Standard network configuration checklist:

ifconfig <interface> (check IP address)
ping [www.google.com](www.google.com) (note error message - what is it ??)

If DNS is the issue:

cat /etc/resolv.conf

(It's probably pointing to your router)

ping the server pointed to in /etc/resolv.conf

If DNS is not the issue, and/or you have a name server and can't pong it:

netstat -rn

look for the default route (destination 0.0.0.0).  The gateway for this should be your router, and the interface should be your wireless card.  Is there a routing destination for your local LAN ?  Is it using the correct interface ?  Between your router and linux, it should work this stuff out automatically, so check if your router is configured to advertise a default route.  The command 'route add default gateway x.y.z.a' adds a default route.

If this doesn't get you there, then post again with the output from

ifconfig <wireless interface>
cat /etc/resolv.conf
netstat -rn
ping [www.google.com](www.google.com)

and someone should be able to tell what's wrong.

cheers

---

### Post by BlacKoffee on 2006-02-23
Okay, when I ping [www.google.com](www.google.com), I get...
> "ping: unknown host www.google.com"

cat etc/resolv.conf returns:
> "cat: etc/resolv.conf: No such file or directory"

netstat -rn returned:

```
Destination     Gateway    Genmask          Flags   MSS Window  irtt    Iface  
192.168.2.0    0.0.0.0      255.255.255.0   U           0  0             0    ath0
192.168.2.0    0.0.0.0      255.255.255.0   U           0  0             0    ath0
```

Does this help anyone? I'm so confused o_O

---

### Post by Kensey on 2006-02-23
OK, what you say about your other PCs dropping off the Internet when you bring the wireless on this one up sounds just like an IP conflict with the router... but the IPs you list look OK.  Although it's a little odd for a router to use .36 as its IP on its own subnet instead of .1.  You say "base station desktop" though.  What is your actual network structure?  Does it look like this (pardon bad ASCII drawing):

```
Internet <---> router <---> desktop
                        |-> laptop
                        +-> Ubuntu
```

or like this:

```
Internet <---> desktop <---> router <---> laptop
                                      +-> Ubuntu
```

or something else completely?

Tell us what output you get from:

ifconfig ath0

(what IP address and subnet mask you have)

iwconfig ath0

(primarily whether it shows "unassociated" or "802.11b" or "802.11g" in the upper left of the result block, and what the signal strength is in the lower left)

What happens when you ping another machine on your network?

What happens when you bring the ath0 interface up and run:

dhclient ath0

?

What subnet and subnet mask is the router using? -- Joe

---

### Post by BlacKoffee on 2006-02-23
My router set up looks like the first thing you typed. The internet goes into the router, which is wired to my desktop, then services my laptop and ubuntu wirelessly. 

ifconfig ath0 returns 192.168.2.12 as the IP adress and 255.255.255.0 as the subnet mask.

iwconfig ath0 returns IEEE 802.11g and 34/94 as the Link Quality (I'm assuming this is connection strength) transfering at 11Mbs. 

When I ping my laptop, it returns:
```

64 bytes from 192.168.2.2: icmp_seq=1 ttl:128 time=3.40 ms
```

It then repeats in a loop with icmp_seq=x increasing incrementally and the times fluctuating. 

I don't know how to bring up the ath0 interface,unless you're talking about just going under the System>Administration>Networking tabs. And if that's the case, I don't know how to run dhclient from there. Sorry :S

The subnet and subnet mask on the router is 255.255.255.255 and 255.255.255.0, I think. Either that, or they're both 255.255.255.0.

Does this help?

Aaron

---

### Post by BlacKoffee on 2006-02-27
Does anyone have any clue what's going on? Please help!

---

