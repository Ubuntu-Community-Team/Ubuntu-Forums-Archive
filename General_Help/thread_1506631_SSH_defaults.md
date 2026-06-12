---
title: "SSH defaults"
date: 2010-06-10
forum: General Help
---

### Post by joeyjoejo on 2010-06-10
Hi All,

I just wanted to ask if anyone knows if ubuntu is set up to allow SSH connections over the internet?

The background is that my computer got left on unattended for ages, and I was worried someone might have had a go at hacking (I hear it's very common for people to try and use SSH to get into systems remotely). Even though my password is strong, I still would rather not have the attack vector open.

all best,
Joe

---

### Post by spiky001 on 2010-06-10
why not go here and have it checked
[http://nmap-online.com/](http://nmap-online.com/)

---

### Post by nirvana21 on 2010-06-10
> **spiky001 said:**
> why not go here and have it checked
[http://nmap-online.com/](http://nmap-online.com/)

Can anyone explain exactly what this does? I did a scan and I am not really sure what I am looking at. It does say that all 100 ports are filtered. I have 2 computers connected to the Internet right now, both Ubuntu 9.04, yet it says only one host is up.

I am not really familiar with networking. I understand ports but that is about it. I have openssh installed on a system as does the original poster.

Thanks!

---

### Post by spiky001 on 2010-06-10
nmap scanner is what is used by most ppl to scan networks, it will show which ports are visible to the scanner i,e if you use ssh on standard port it will show port 22 so if no ports are shown then non can be attacked, it shows you are online but all ports closed.

---

### Post by nirvana21 on 2010-06-10
> **spiky001 said:**
> nmap scanner is what is used by most ppl to scan networks, it will show which ports are visible to the scanner i,e if you use ssh on standard port it will show port 22 so if no ports are shown then non can be attacked, it shows you are online but all ports closed.

So if I went into my router and forwarded port 22 (assuming ssh is running on port 22) for the LAN address of the computer running ssh, that port would pop up in that test? So that would be true for any other service, such as FTP? I just want to make sure I really understand this. Thanks!!

---

### Post by spiky001 on 2010-06-10
I presume so i scanned mine no ports (thats with firewall)  then without FW showed 2 ports open

---

### Post by jerome1232 on 2010-06-10
By default sshd is configured to allow connections from anywhere, however if, as most people are, your computer is behind a router and that router has not been configured by you to forward whatever port your computer is using for ssh, then no one outside your lan can connect to the ssh server.


@nirvana21, kind of the same thing those 2 computers are probably hooked up to a router which translates everything into one ip that you use to connect to the internet with. So as far as the internet is concerned your entire lan (be it 2 computers or 500) is one address.

a little diagram

```


computer 1 (192.168.1.1) ---------\
                                   \
computer 2 (192.168.1.2) -----------| (192.168.1.254 ) router (75.54.35.255) ----- Internet
```

In that example as far as any computer outside your lan is concerned they are talking to 75.54.35.255 and only know of that one address. Your router does the job of routing traffic directed at 75.54.35.255 to the correct computer.

---

### Post by joeyjoejo on 2010-06-10
it claimed that all 100 ports are filtered - is that really just a regular implication of having a router that I've not set up in any depth?

I just have a plain installation without a firewall or anything. Is that enough in Ubuntu? (I'd never do that in windows, but I would be fairly confident with fedora or some variety of BSD)

[EDIT: This post also seems of interest to the current topic: [http://ubuntuforums.org/showthread.php?t=1260725](http://ubuntuforums.org/showthread.php?t=1260725) ]

---

### Post by spiky001 on 2010-06-10
I have googled this it seems it,s something to do with how nmap deals with port scanning sorry i,m no expert. I have been led to believe linux ports are closed by default unless opened mine shows 2 open maybe 6 filtered I know 2 are open the others I have not touched but firewall hides all when on

---

### Post by joeyjoejo on 2010-06-10
And one more thing, if I may...

the fact that it says that all 100 ports are filtered, what does that mean for port 80 (HTTP) - surely the mere fact that a computer is online is sufficient to show that data can pass to and from there?

I'm afraid this isn't a topic I know anything about

---

### Post by HeirPixel on 2010-06-10
Nmap is trying to connect to a service on the ports scanned. It sees your modem's IP and thinks your router is the host (not knowing the difference between that and a computer).

If your router is blocking all requests on all ports, that's not a bad thing unless you WANT to serve something through it. even port 80 will show blocked because Nmap is *requesting* content on that port, not sending it.

If you wanted to test against all ports on your computer, you could individually map each port in your router settings if you were masochistic. The better option would be setting up a DMZ. From Netgear:

[INDENT]Specifying a Default DMZ Server allows you to set up a computer or server that is available to anyone on the Internet for services that you haven't defined. There are security issues with doing this, so only do this if you're willing to risk open access. If you do not assign a Default DMZ Server, the router discards any incoming service requests which are undefined.[/INDENT]

Just be sure to disable the DMZ after running your scan ;)

---

### Post by BoneKracker on 2010-06-10
> **spiky001 said:**
> I have googled this it seems it,s something to do with how nmap deals with port scanning sorry i,m no expert. I have been led to believe linux ports are closed by default unless opened mine shows 2 open maybe 6 filtered I know 2 are open the others I have not touched but firewall hides all when on

If you are using a gateway device (e.g. firewall/router) that performs NAT and not using IPv6, then from the perspective of an external nmap scan, it doesn't matter what ports you have open or closed on your linux boxes because it's never going to see them.  It's only going to see the machine that's answering to the IP address it scanned (the router).

You should still configure security in depth.  You have some degree of control from the sshd configuration file's "listen_address" setting (which is normally set to listen to everything by default).  Ubuntu probably also has tcp wrappers enabled; if so, you have additional control through /etc/hosts.allow and /etc/hosts.deny.  If you are running iptables on the sshd host, you have further control there.  Any or all of those three things can be used to restrict access to sshd from the Internet (in addition to any firewall running on your internet gateway).

I don't know what Ubuntu does, but sshd should not be starting by default.  It should require explicit user action to start it or to set it to start automatically.  If there is an /etc/xinetd.d/sshd file, that should also be disabled by default.

---

### Post by jerome1232 on 2010-06-10
There are different types of traffic.

Inbound and Outbound.

When you goto a website you send an outbound packet and establish an ongoing connection that your router (and firewall) knows you explicitly requested, and they allow traffic to flow between you and the host as the two computers have negotiated it to happen.


Inbound traffic is when another computer tries to request a service from your computer. Which your router knows your computer hasn't asked for so it will just drop the traffic, or if your router was configured to forward all inbound traffic on that particular port it will pass the packet on to your computer, which can then decide how to handle it (drop it, rejecting it, or perhaps a service such as ssh will accept it and start a session with the other computer)

Hopefully that's a mostly correct very general sum of how it works.

---

### Post by joeyjoejo on 2010-06-11
thanks guys, that's a really good explanation, and I think I feel a fair bit safer now. 

I do agree with BoneKracker though, ssh should be disabled by default. If you want to use it, you can switch it on, but those people who don't want to use it are exactly those who need protecting from it the most.

---

### Post by jerome1232 on 2010-06-11
an SSH server is not installed at all by default. Only an ssh client.

---

### Post by BoneKracker on 2010-06-11
> **jerome1232 said:**
> an SSH server is not installed at all by default. Only an ssh client.
Even better.

---

