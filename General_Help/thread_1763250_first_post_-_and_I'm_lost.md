---
title: "first post - and I'm lost"
date: 2011-05-20
forum: General Help
---

### Post by UNOE on 2011-05-20
I've used Ubuntu only a few time in the past few years. At times I completly gave up on it. I've been able to do simple things like Samba server, and setup folding@home client. I often go through turorials in the terminal and get through 10-15 commands then I get stuck and never able to use what I want to use. Now I have a dedicated Ubuntu box that I'm VNC'ing into thats local and is working as my NAS with samba for a few months now. I want to use this for all my server needs which brings me to my questions.
 
I really want to try to get VPN server working on this box. A dedicated VPN server. I want to use it for my a few phones. I went threw a few tutorials already none worked. I'm wondering if there is a graphical way to do this because the command lines are killing me (I know you all pride yourself). It just really a pain I can do this on windows in a few minutes. I'm sure most of you can get this working on ubuntu in minutes too but I just spent 3 hours trying to get this working but have no idea what I'm doing wrong.
 
I have a second question but I guess this is only if I never get VPN working. Is there a way to keep it as a local NAS that has no access to out side traffic. And would there be away to even with VPN working to limit all traffic to local with exception to the VPN. I imagine that isn't possible but just thought I should ask.

---

### Post by Paqman on 2011-05-20
> **UNOE said:**
> I've been able to do simple things like Samba server

That's a step on from what i'd call "simple", sounds like you've been doing some moderately technical stuff. Don't worry if you need a hand with it, that's what the community is for.

> I want to use it for my a few phones.

Maybe it's me, but I don't really understand what you're trying to do here.

So to sum up:
[LIST=1]
[*]You have a desktop machine with Ubuntu installed, not a server/headless, hence the desire to do this through a GUI?
[*]You want to get VPN access to this, but only locally?
[/LIST]

Does it have to be a VPN? If it's just local there's easier ways to share files. Do you have some particular client or OS that you'll be using to connect to the NAS?

---

### Post by UNOE on 2011-05-20
> **Paqman said:**
> That's a step on from what i'd call "simple", sounds like you've been doing some moderately technical stuff. Don't worry if you need a hand with it, that's what the community is for.
 
 
 
Maybe it's me, but I don't really understand what you're trying to do here.
 

So to sum up:[LIST=1]
[*]You have a desktop machine with Ubuntu installed, not a server/headless, hence the desire to do this through a GUI?
[*]You want to get VPN access to this, but only locally?
[/LIST]
Does it have to be a VPN? If it's just local there's easier ways to share files. Do you have some particular client or OS that you'll be using to connect to the NAS?
 Thanks, the local server is already set up with file server and mounted drive on my wifes, moms, roomates, labtop, and my computer that is working great now for months.  If I can't get VPN working I want to set this server to only run local, but I guess that I shouldn't worry about that yet.  Really I'm going to put some good effort into the VPN for now if that works then I will forget the whole local thing.  I want the VPN to connect a couple phones too.  Currently I'm set up with a dynamic address and OpenDNS for filtering adult content threw the OpenDNS.  So everything going threw my router has Adult content filtering.  I want a VPN so the phones will benifit from the Adult content filtering as well.  So since I already have everything all setup including my dynamic address.  All I really need is a VPN server.  I just need one of the three L2TP, PPTP, or Ipsec.  I know I could do this on window quickly.  But my ubuntu computer is already on 24/7 so it would make most sense for me to get VPN on this machine.

---

### Post by UNOE on 2011-05-20
Bump

---

### Post by UNOE on 2011-05-20
did I post this in the wrong place ?

---

### Post by josephmills on 2011-05-20
> **UNOE said:**
> did I post this in the wrong place ?

I am sorry but I can not answer your question but if you did want to move this thread you could contact a mod and ask him/her/z to move it for you I would like to say welcome to UbuntuForums hope this gets solved :) also do you like ssh?

---

### Post by UNOE on 2011-05-23
Bump
I guess I need this movied No help yet....

---

### Post by dash10 on 2011-05-23
I'd say so -- this seems fairly advanced for the Beginner Talk forum.

---

### Post by jtarin on 2011-05-23
How to....[PPTP VPN Server.]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")and [Here]("http://eubolist.wordpress.com/2010/01/28/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx/").

---

### Post by UNOE on 2011-05-24
> **jtarin said:**
> How to....[PPTP VPN Server.]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")and [Here]("http://eubolist.wordpress.com/2010/01/28/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx/").
 
This worked for me thanks so much

---

### Post by UNOE on 2011-05-24
> **jtarin said:**
> How to....[PPTP VPN Server.]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")and [Here]("http://eubolist.wordpress.com/2010/01/28/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx/").
 
Spoke to soon even though it connects no traffic seems to be routing threw.

---

### Post by jtarin on 2011-05-24
Excellent....glad to help.Good Luck to ya!Mark this thread as solved if you would. It will help others with this problem.

---

### Post by jtarin on 2011-05-24
[Re-check #13]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")

UPDATE(2010-07-18): If connecting to the vpn-server goes well but you can&#8217;t connect to the internet you might want to try uncommenting the ms-dns entries in /etc/ppp/pptpd-options so it looks like this:

    ms-dns 208.67.222.222
    ms-dns 208.67.220.220

---

### Post by UNOE on 2011-05-24
> **jtarin said:**
> [Re-check #13]("http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html")
 
UPDATE(2010-07-18): If connecting to the vpn-server goes well but you can&#8217;t connect to the internet you might want to try uncommenting the ms-dns entries in /etc/ppp/pptpd-options so it looks like this:
 
ms-dns 208.67.222.222
ms-dns 208.67.220.220
 
I just tested VNC through the phone when I'm connected to my VPN on my phone and I can VNC into other computer on the network from my phone to typing local addresses such as 192.168.1.xx, over 3G.  So I know it is fowarding traffic to atless my router. So I think it is something with DNS as you stated ill look into that thanks.  Ill mark as solved when traffic is fowarding properly.

---

### Post by jtarin on 2011-05-24
Those two listed are OpenDNS servers. You can also try Googles Public servers. 8.8.8.8, 8.8.4.4

---

### Post by UNOE on 2011-05-25
> **jtarin said:**
> Those two listed are OpenDNS servers. You can also try Googles Public servers. 8.8.8.8, 8.8.4.4
 
Thanks again but the Adding the DNS's didn't work.
Its a different problem.  Not sure what.  Since im such a newbie to Linx I'm sure im doing something wrong.  Even though through VPN I was able to view my computers through VNC.  I could not log onto my router which makes me think it does have something to do with ipv4.

---

### Post by CharlesA on 2011-05-25
Moved to General Help, maybe you'll get more help there. :)

---

### Post by UNOE on 2011-05-25
> **CharlesA said:**
> Moved to General Help, maybe you'll get more help there. :)
 
Thanks for the move.

---

### Post by jtarin on 2011-05-25
Check your router to see if it is forwarding properly and set up with those DNS.

---

### Post by UNOE on 2011-05-26
> **jtarin said:**
> Check your router to see if it is forwarding properly and set up with those DNS.
 
Forwarding the ports was the first thing I did.  The DNS didn't do anything.

---

### Post by jtarin on 2011-05-26
When your connected in a terminal execute and post the results from the command "route -n" .

---

### Post by UNOE on 2011-05-26
> **jtarin said:**
> When your connected in a terminal execute and post the results from the command "route -n" .
 
[I]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.224 U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1[/I]

 
**BTW, I changed these three lines to say eth1 from eth0 already.**
*iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE*
[I]iptables -A INPUT -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
iptables -A INPUT -i eth1 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP[/I]

---

### Post by jtarin on 2011-05-26
You have more than one ethernet card?

---

### Post by UNOE on 2011-05-26
> **jtarin said:**
> You have more than one ethernet card?
 
Yes, onboard and pcie gigabit card. I use the gigabit card.

---

### Post by jtarin on 2011-05-26
Have you tested to see if your ports are forwarded correctly? I know you said you did it, but did you test them?

---

### Post by UNOE on 2011-05-27
> **jtarin said:**
> Have you tested to see if your ports are forwarded correctly? I know you said you did it, but did you test them?
 
I just got to say thanks for all your help so far.  Reason I don't think its the Forward port is because I can log onto VPN through the phone on 3g network.  And I can load my other computers through VNC and access stuff locally.  Only the internet and browser doesn't work.  I say this because I can't log onto my router which uses the browser.  But the Local connections to VNC through VPN over Att 3G network works perfectly.  I don't see how this would be a port issue.  But maybe I'm not seeing anything.  I don't know how to test the port because I have never had a port that the router was saying it was forwarding not actually forwarding.
 
But honestly I can't really say how much help you been.  Does this forum have a place to add rep or something along those lines cause you sure deserve it.

---

### Post by jtarin on 2011-05-27
[This link I gave you earlier]("http://eubolist.wordpress.com/2010/01/28/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx/"),,,,,did you read the comments section also? Informative.To check for ports forwarded install "network tools"....it's in the repositories. Use Synaptic. After installation you'll find it under administration. There's a "portscan" tab...us it to check your ports. Use the address of your router.
I might try this myself instead of VNC. I'll let you know if I do.

---

### Post by wlraider70 on 2011-05-30
are you getting anything in /var/log/auth.log 

I'm messing with a L2TP issues and found there were logs there that I didn't realize. I don't know if it would be the same for you.

---

