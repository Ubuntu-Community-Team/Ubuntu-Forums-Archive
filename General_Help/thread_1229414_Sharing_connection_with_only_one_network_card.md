---
title: "Sharing connection with only one network card"
date: 2009-08-02
forum: General Help
---

### Post by Lockheed on 2009-08-02
The ISP cable enters my flat and goes to two computers.
ISP assigned only 1 IP so only one computer can have internet at any time.

I am looking for one of two solutions on ubuntu.

1. Internet connection sharing set up on one computer which requires only ONE network card in this computer. It means the same card deals with external and internal network.
This is what I have not been able to achieve on Windows.

2. Proxy server which also works with only one network card. This is what I used on Windows (ProxyPlus program). I set another computer's IP into the same IP range as my main computer and although it was unable to connect to the internet, it could connect to my main computer and access internet through its proxy.

So, is any of the to possible on Ubuntu? 
If so, how do I go about it?

---

### Post by DeMus on 2009-08-02
> **Lockheed said:**
> The ISP cable enters my flat and spreads on the router into two computers.
ISP assigned only 1 IP so only one computer can have internet at any time.

I am looking for one of two solutions on ubuntu.

1. Internet connection sharing set up on one computer which requires only ONE network card in this computer. It means the same card deals with external and internal network.
This is what I have not been able to achieve on Windows.

2. Proxy server which also works with only one network card. This is what I used on Windows (ProxyPlus program). I set another computer's IP into the same IP range as my main computer and although it was unable to connect to the internet, it could connect to my main computer and access internet through its proxy.

So, is any of the to possible on Ubuntu? 
If so, how do I go about it?

When you have connected your ISP cable to a router you should have no problems connecting more than 1 computer to the internt at one time.
Yes, your ISP gave you 1 IP number, that's right. That number is taken by the router on it's wan side (internet side)
Then the signal goes through the router to the ethernet side. It gives you as many IP numbers as you need for all your PC's.
When you set your PC's to s DHCP network connection the PC's will get their IP number from the router. This will probably be a number in the 192.168.x.x series, or the 10.0.0.x series, depending on the type of router.
I have had 5 PC's at home all connecting to the internet simultaneously and had no problems what so ever.

---

### Post by Lockheed on 2009-08-02
I made a serious mistake by stating it is a router. Of course, there would be no problem there.

But it is just a switch.

---

### Post by DeMus on 2009-08-02
> **Lockheed said:**
> I made a serious mistake by stating it is a router. Of course, there would be no problem there.

But it is just a switch.

OK, yes, now I understand your problem. I know it'll cost you a few bucks, but try to get a simple router and your problems are over.
That's what I did: my internet modem has 1 ethernet connection which I connected to a router and from there to my PC's.
Routers are not that expensive anymore. Just look around.

---

### Post by Lockheed on 2009-08-02
I know that would solve the problem, but I am looking for a software solution here.

---

### Post by Lockheed on 2009-08-04
Bump

---

### Post by Lockheed on 2009-08-06
Seriously? There is no way to do it in Ubuntu?

---

### Post by Lockheed on 2009-08-09
One would think Linux can do more than Windows, while more and more often I learn it is the other way around...

---

### Post by Lockheed on 2009-08-18
But seriously?

---

### Post by LowSky on 2009-08-18
Maybe I dont under stand what you are trying to do, but Im going to try to repeat it in American English.

You want to have to computers able to use the same internet connections that sprouts out of the wall. correct?


look, you need a router, or an extra Ethernet card (or wifi cards) to set up a PC bridge, either way you need to buy equipment. Just because Linux can be more customizable doesn't mean we can do things out of thin air.

A router works best can be purchased for about $20US and the simplest  answer to your problems.

---

### Post by Lockheed on 2009-08-18
I know what routers costs and I'm not buying one.

No thin air necessary as it works perfectly under windows. ISP cable gets separated on transparent switch (no routing function) into computer A, computer B and voip telephone.

1:0 for windows here?

---

### Post by buchan on 2009-08-18
I'm afraid its 0:0 for both here, its physically impossible to do what you are after without either a second network card in one of your machines or a router of some sort.  

A router establishes a network that is separate from your ISPs network so that it can translate (NAT) the traffic between the two effectively.  (Sorry for lack of a better education that's the best way I can explain it)

If one of your computers had more than one network card it would be possible to turn it into a "router" as well, no matter if you were using windows or Linux.  

Have a look at [this]("http://www.mts.net/~hooch/images/computer_network_diagram.png") pic, it gives a simple outline of what you are are trying to achieve.

---

### Post by Lockheed on 2009-08-18
Nope, it is 1:0 for Windows cause on XP and 7 I've been using option no.2 from my first post since like 4 years.

I didn't think linux would get beaten up by windows in the networking department but there it is.

---

### Post by buchan on 2009-08-18
I need to understand this better ...

1. Your ISP gives you a single IP address?

2. You have two computers each with a single network card?

3. Both of these two computers are plugged into the same network SWITCH?

4 Both of these machines can access the net at the same time?

If they are running windows and have access to the net can you give me the IP addresses just for so I can see what they are?  
All I would like to see are the first two sets of numbers eg: 111.111.  

I'm extremely curious to know how this works.  
Are both machines set to DHCP addresses or is one set up manually?
If the second system is set up manually what are the settings?

---

### Post by dcstar on 2009-08-19
> **buchan said:**
> I'm afraid its 0:0 for both here, its physically impossible to do what you are after without either a second network card in one of your machines or a router of some sort.  
.........
Rubbish.

Is it really too hard for people to do a simple forum search on "share internet connection"???

[http://ubuntuforums.org/showthread.php?t=91370&highlight=share+internet+connection](http://ubuntuforums.org/showthread.php?t=91370&highlight=share+internet+connection)

---

### Post by hibliss on 2009-08-19
What is the model of the switch you are using? Linux networking is light years beyond Windows, which is why most routers, especially commerical routers run Linux.

---

### Post by Lockheed on 2009-08-19
> **buchan said:**
> I need to understand this better ...

1. Your ISP gives you a single IP address?

2. You have two computers each with a single network card?

3. Both of these two computers are plugged into the same network SWITCH?

4 Both of these machines can access the net at the same time?

1. Yes.
2. Each computer has one network card.
3. Yes.
4. Yes and No.

Computer A is using IP from ISP. Computer B is using the same network settings except the IP which is one of the unused IPs from the same range as IP no1. Computer B cannot access internet directly even though it is in the same network as A and 5000 other machines served by this ISP. However, it can ping computer A. Computer A hosts HTTP proxy which is being used by B to access internet.

> Is it really too hard for people to do a simple forum search on "share internet connection"???

[http://ubuntuforums.org/showthread.p...net+connection](http://ubuntuforums.org/showthread.p...net+connection)
What does it have to do with my question?

> What is the model of the switch you are using? Linux networking is light years beyond Windows, which is why most routers, especially commerical routers run Linux.
**ES-3105P**
[IMG]http://www.svp.co.uk/custom/images/products/hw221.jpg[/IMG]

---

### Post by hibliss on 2009-08-19
> **Lockheed said:**
> 1. Yes.
2. Each computer has one network card.
3. Yes.
4. Yes and No.

Computer A is using IP from ISP. Computer B is using the same network settings except the IP which is one of the unused IPs from the same range as IP no1. Computer B cannot access internet directly even though it is in the same network as A and 5000 other machines served by this ISP. However, it can ping computer A. Computer A hosts HTTP proxy which is being used by B to access internet.


What does it have to do with my question?


**ES-3105P**
[IMG]http://www.svp.co.uk/custom/images/products/hw221.jpg[/IMG]


There is a BASH script in this link that looks like it will do the job with your current setup -- [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

```
#!/bin/sh
#
# internet connection sharing wlan0 is the gate way
# eth0 is the lan port this might use a straight ethernet cable to a router wan port or a switch or a single PC
# 192.168.2.2 is the port that is being used by the lan for access I changed it to 192.168.2.254 and set fixed addresses for the wan and router
#
# change wlan0 to ppp0 and you can use this for mobile broadband connection sharing
#
ifconfig eth0 up"
ifconfig eth0 192.168.2.1
echo “1” > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.2
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p udp -m multiport --dports 88,3074 -j ACCEPT
```

You are going to need to tweak it a bit for your needs, but the instructions are built in to the script. Once you get it working you can set the script to run at boot.

---

### Post by Lockheed on 2009-08-20
> **hibliss said:**
> There is a BASH script in this link that looks like it will do the job with your current setup

Correct me if I am wrong but doesn't it contradict the purpose of this thread:
> You will need two network cards in the gateway computer

---

### Post by hibliss on 2009-08-20
Yeah you are wrong. You read 4 paragraphs and gave up.

The solution I am offering is separate from that, and at the bottom of the page. I provided the link so you could read the source, but the BASH script should be all you need.

Why don't you try it?

---

### Post by Lockheed on 2009-08-20
I must say I read it throughout and still don't know how can I use it in my situation.
Any solution provided there requires either two ethernet cards or one ethernet and one wifi card.

What I am looking to use only ONE eth card and nothing more.

---

### Post by sefs on 2009-08-20
Install virtualbox/vmware on computer A, set up ubuntu in the vm, with 2 virtual nics, configure the vm as a router (google to find out how), and then set both computer A, and B to use that VM as their gate way.

You won't have to buy anything.

---

### Post by Lockheed on 2009-08-20
Well, that's some solution but... 

How about a simple proxy server which can receive and send connections at the same interface? Just like ProxyPlus for Windows.

---

### Post by sefs on 2009-08-20
> **Lockheed said:**
> Well, that's some solution but... 

How about a simple proxy server which can receive and send connections at the same interface? Just like ProxyPlus for Windows.

That's the great thing about open source if it doesn't exist you can write it, I think ubuntu comes with a gcc.  It shouldn't be too difficult as you just need a simple one.

---

### Post by Lockheed on 2009-08-21
Well, my programming knowledge boils down to ACLogo and self-taught QuakeC so I gonna pass on that.

---

### Post by mbaas on 2009-08-21
Well, you could try using an IP alias, [here]("http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html")'s something about that. And then see if u can use squid on the alias ip. Don't no if it 'll work though, never tried it before.

---

### Post by Lockheed on 2009-08-21
Ooo, this alias-thing looks interesting. Thanks.

---

### Post by mbaas on 2009-08-21
Just tested on a Fedora 11 box lying around here, seems to work, however, setting up iptables and ip alias is somewhat different than setting up iptables using 2 nic's. I found [this]("http://www.review-ninja.com/2008/08/ubuntu-linux-multiple-ip-ip-aliasing.html") with some information about it. Unfortunately i don't have a whole lot of time atm, so google is your friend if you want more info =)

---

