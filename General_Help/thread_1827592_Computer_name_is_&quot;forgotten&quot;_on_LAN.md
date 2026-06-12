---
title: "Computer name is &quot;forgotten&quot; on LAN"
date: 2011-08-18
forum: General Help
---

### Post by paxxus on 2011-08-18
I'm running ubuntu 10.04 and what I see is that after a few days up-time other computers on our LAN cannot resolve my ubuntu name anymore. This is critical since my NFS mounts stop working (my computer name is mentioned in the /etc/exports on the NFS server). My ubuntu is connected via DHCP.

Is there some sort of refresh mechanism which needs to be configured in ubuntu?

---

### Post by paxxus on 2011-08-18
Some more info:

```
@ /home/sk
cph-emp-sk ? sudo dhclient eth0
[sudo] password for sk: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/b8:ac:6f:9c:69:bb
Sending on   LPF/eth0/b8:ac:6f:9c:69:bb
Sending on   Socket/fallback
DHCPREQUEST of 10.240.10.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.240.10.100 from 10.240.1.60
bound to 10.240.10.100 -- renewal in 326197 seconds.
```I edited the file /etc/dhcp3/dhclient.conf to include the line:

send dhcp-lease-time 3600;

But as you can see from above I still get renewal in 326197 seconds.

---

### Post by Zill on 2011-08-18
> **paxxus said:**
> ...My ubuntu is connected via DHCP...
My understanding is that it is much easier to use NFS with static, rather than dynamic, IP addresses.

If your network worked OK previously with DHCP then, presumably, everything was configured correctly and there must be some other problem.

However, if this is a newly configured system then I suggest you may get better results by using static IP addresses, defined in /etc/network/interfaces.  Then use the fixed IP addresses for all NFS configuration files, rather than hostnames.  You can, of course, specify ranges of IP addresses, rather than unique addresses if necessary.

---

### Post by Morbius1 on 2011-08-18
Another way to achieve static ip addresses you might want to consider is having your router "reserve" an ip address for each machine. That way you can leave each machine as it is - a dhcp client - and have the router do all the work. Most routers call it "DHCP Reservation" but it can go by other names so check out the manual.

Just something to consider.

---

### Post by paxxus on 2011-08-18
Thanks for your answer Zill (and Morbius1). Unfortunately I do not have control over the LAN infrastructure so I don't think I can use static IPs. In any case, I was told that our local router will always give the same IP again when you renew, so it really shouldn't be an issue.

Most other people here use Windows and those computer names are not forgotten, so there must be something which ensures that the DNS is up to date, something which Windows does and Ubuntu fails to do.

I'm guessing that the default DHCP renewal period is too long on ubuntu, but I can't seen to figure out how to make the period shorter. :confused:

---

### Post by Zill on 2011-08-18
paxxus:  So, just to clarify, are you using an Ubuntu NFS client with a *Windows* NFS server?

Has your LAN *ever* worked correctly with your Ubuntu NFS client machine?

Are there any other Ubuntu (or other Linux machines) on the LAN working correctly with NFS?  If so, are they configured differently?

---

### Post by paxxus on 2011-08-18
The NFS server is a Linux (Suse) machine. I do not have admin rights there.

I don't think the NFS has ever been completely stable on my ubuntu. I used 11.04 (64-bit) for a while, but I was swamped with various other break downs on that distro so I finally downgraded to 10.04 (64-bit). Initially I had major stability issues on my NFS mounts. Then I discovered a work-around where I mount the NFS shares via UDP instead of TCP and it has worked fine ever since (except for this computer name issue).

I don't think I really have a NFS problem anymore now that I use UDP. The root cause is that my computer name is forgotten by the name server. The NFS failure is just a symptom. When, after a few days, the problem occurs I can reboot my ubuntu and after a few seconds the Suse servers (including the NFS server) can resolve my computer name again.

I need to ensure that my computer name does not time-out or whatever in the DNS. The question is how.

 I edited the file /etc/dhcp3/dhclient.conf to include the line:

send dhcp-lease-time 3600;[FONT=monospace]

But when I do sudo dhclient eth0 it still says:[/FONT][FONT=monospace]

[/FONT]```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/b8:ac:6f:9c:69:bb
Sending on   LPF/eth0/b8:ac:6f:9c:69:bb
Sending on   Socket/fallback
DHCPREQUEST of 10.240.10.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.240.10.100 from 10.240.1.60
bound to 10.240.10.100 -- renewal in 328646 seconds.
```[FONT=monospace]

I.e. almost 4 days before reneval instead of the 1 hour I put in the [/FONT]/etc/dhcp3/dhclient.conf  :confused:

---

### Post by Zill on 2011-08-18
paxxus:  Thanks for the additional info.  Unfortunately, other than seeing if a reboot of your client makes your dhcp-lease-time variable "stick", I am right out of ideas.  I only use static IPs on my LAN as I believe DHCP *can* be a problem with NFS. :-(  Hopefully someone with more experience of NFS dynamic addressing will be able to provide some useful help.

---

### Post by paxxus on 2011-08-18
Thanks anyway Zill :)

Let me stress again: I don't think this problem has anything to do with NFS at all. The problem is that my computer name is forgotten on the LAN after a few days. When I reboot ubuntu the other servers can resolve my ubuntu computer name again, presumably because the ubuntu reboot causes an update of the DNS entry in the router or whatever.

How do I ensure that the DNS update / refresh happens at regular intervals?

PS.: It works for the Windows clients, they are not forgotten. So it must be Ubuntu which fails to do some sort of refresh or something.

---

### Post by Zill on 2011-08-18
> **paxxus said:**
> ...It works for the Windows clients, they are not forgotten. So it must be Ubuntu which fails to do some sort of refresh or something.
I am still slightly puzzled here...  You said earlier that "The NFS server is a Linux (Suse) machine."  Presumably the Windows clients are using a separate SMB server, rather than the Suse NFS server.  I don't believe the fact that Windows clients work is particularly relevant to this problem.

Are there any other Ubuntu (or other Linux) clients on the LAN working correctly with NFS? If so, are they configured differently?

---

### Post by paxxus on 2011-08-18
When I say that it works for the Windows clients, I mean that I can log on to any of the Suse servers (for example) and do:

ping <windows-client-name>

And it works even after months of client up-time.

For my Ubuntu client however, after a few days, when I log on to any of the Suse servers and do:

ping <my-ubuntu-client-name>

It can't find it anymore.

I can then reboot my ubuntu and after a few seconds the servers can see my ubuntu name again.

I therefore conclude that the Windows clients are doing something which prevents their names from being flushed from the DNS table, something which Ubuntu fails to do. Question is what. My guess is the DHCP renewal, I just don't know how to fix it :(

---

### Post by bodhi.zazen on 2011-08-18
First, you can set a static ip on the ubuntu client.

Second, you will probably need a dns server on your network or add the ubuntu host to the hosts file of the windows boxen.

I use dnsmasq for small lan.

---

### Post by paxxus on 2011-08-18
I ran for almost one year on a Windows 7 installation on the same machine. I now have ubuntu dual boot on that same machine, I even have the same machine name in ubuntu as in Windows 7. Why should I need to fiddle with static IPs etc. when the DHCP setup works fine in Windows 7?

As I said, when I reboot the ubuntu everything works fine for a few days. Can't I just configure ububtu to do, at regular intervals, whatever it is it does at boot time?

I'd really appreciate if anyone knows how to force a DHCP renewal event at regular intervals from the ubuntu client side.

:D

---

### Post by tredegar on 2011-08-18
Next time this happens, please confirm that the IP assigned to your computer has indeed changed from what you think it should be.

Run **ifconfig** on your machine to see what its LAN IP has changed to.

If it has really changed, then the fault lies with the DNS server you are using.

---

### Post by paxxus on 2011-08-18
tredegar: I can answer this right now. I don't lose IP, in fact the ubuntu machine works fine, I can log in to other machines etc. It's just that the NAME of my ubuntu becomes unknown to OTHER machines after a few days. I can still ping the ubuntu IP directly, the IP doesn't change.

---

### Post by tredegar on 2011-08-18
Thanks.
I have a static IP, but I disabled that and asked my router for a dhcp address.
I got one, but when I look at my router's "Connected devices", my PC's name is "UNKNOWN". So, same problem as you have.

A little searching tells me to edit **/etc/dhcp3/dhclient.conf** and put the line:
```
send host-name "*laptop*";
```
(Add it, or uncomment and edit it)

This did not help when I requested a new lease, router still says "UNKNOWN".

Maybe I need to completely restart networking, but I am watching the news!

I'll catch up later, but maybe this info helps you a little in the meantime.

---

### Post by paxxus on 2011-08-18
tredegar: Well, I'm not sure it is exactly the same problem you see, bacause for me it DOES work after a reboot, it's just that it stops working after a few days and the other servers become unable to resolve my ubuntu computer name.

The send host-name command is un-commented by default in the config file with an argument of "<hostname>" if I remember correctly, I'm assuming that <hostname> is being automatically replaced with the actual machine name by the DHCP client.

---

### Post by bodhi.zazen on 2011-08-18
You need a dns server ;)

---

### Post by paxxus on 2011-08-18
Any answers which revolve around the LAN infrastructure, DNS server, static IP and what not, fail to consider the fact that it WORKS for multiple Windows DHCP clients, I can ping all of the Windows clients from any server no matter how many days have passed. The problem is on my ubuntu, I cannot come to any other conclusion given the observations. In any case I do not have authority to change the LAN setup.

---

### Post by bodhi.zazen on 2011-08-18
> **paxxus said:**
> Any answers which revolve around the LAN infrastructure, DNS server, static IP and what not, fail to consider the fact that it WORKS for multiple Windows DHCP clients, I can ping all of the Windows clients from any server no matter how many days have passed. The problem is on my ubuntu, I cannot come to any other conclusion given the observations. In any case I do not have authority to change the LAN setup.

But Ubuntu is not windows and ubuntu does not announce itself.

You will need a dns server or you will need to update the windows host file(s) on each client.

You can also look at this : [http://oreilly.com/openbook/samba/book/ch07_03.html](http://oreilly.com/openbook/samba/book/ch07_03.html)

But if you do not have control of your network, you will then need to talk to you network administrator.

---

### Post by tredegar on 2011-08-18
@paxxus:> I'm assuming that <hostname> is being automatically replaced with the actual machine name by the DHCP client.
I have learnt *never* to make assumptions, but check, and check again. I put the line```
send host-name "laptop";
```
into **/etc/dhcp3/dhclient.conf** and restarted networking (once the BBC had finished ;)). No joy: the router still does not register my hostname.

@bodhi: paxxus wants to send his hostname to the dhcp server so other (win/linux) computers know where he is by hostname. This apparently works at boot, then fails after a few days.

I have a static IP address, I disabled this. Now, using dhcp3 to get a dynamic IP from my router (Netgear DG834G) I can see my router records my MAC address and allocated LAN IP, but my PC's name is "UNKNOWN", so I have the same problem with dhcp as paxxus. The router does not know my hostname.

The question boils down to this:

How do I/we get ubuntu's dhcp client to send my hostname to the router when the dhcp lease is negotiated?

In paxxus's case, it works (once, at boot) then dies later. If he reboots, it's OK for another few days, then dies. For me (10.04) dhcp  *never* tells my router my hostname.

My brother connected his 11.04 PC to my network the other day, and i noticed to my surprise, that the router displayed his PC's hostname, not just his (static) IP. I didn't really care, because with static IPs everything works, and we are each in each other's **/etc/hostname** so address resolution is easy on my static network.

Something is at fault.

From the documentation, putting this into **/etc/network/interfaces**:
```
auto eth0
iface eth0 inet dhcp
hostname *laptop*

```
*should* let the dhcp server know my hostname. It does not.

With all this messing around, I am quite surprised that I am still connected.
I'll reset things as they were.

Addendum: I see you have both added to this thread.
@bodhi.zazen> But Ubuntu is not windows and ubuntu does not announce itself.
Then why does it work for him at boot (router knows his hostname), but then forget it? It's a linux router. This should not happen.

---

### Post by paxxus on 2011-08-18
tredegar, you sumarized the problem perfectly :P

---

### Post by bodhi.zazen on 2011-08-18
> **tredegar said:**
> Then why does it work for him at boot (router knows his hostname), but then forget it? It's a linux router. This should not happen.

> **paxxus said:**
> tredegar, you sumarized the problem perfectly :P

I understand the problem, but without access to the router or administrative rights on the network I am not sure how you are going to solve the problem.

It works at first because Ubuntu announces it's hostname when negotiating the dhcp protocol, but the router is not acting as a dns server and it forgets the hostname at some point in time. This would be trivial to solve if one had access to the router configuration.

Did you read the link I gave you about winns ? Ubuntu does not announce itself on the network the way Windows machines do.

You can try to see of Avahi is working.

[http://askubuntu.com/questions/19590/how-do-i-share-nfs-mounts-over-zeroconf](http://askubuntu.com/questions/19590/how-do-i-share-nfs-mounts-over-zeroconf)

I have had mixed results with Avahi.

You then use your ubuntu_hostname.local rather then just ubuntu_hostname

---

### Post by paxxus on 2011-08-18
Thanks bodhi, I will study the links you gave.

To give a little background, my office have externally hired IT support costing an arm and a leg. My office desktop came with Windows installed and that's what is supported. I can't really expect to get support for my own ubuntu hacking and demand all kinds of special router setup just for me when everybody else can use the default DHCP setup. It's already borderline that I'm dual booting ubuntu. In other words, I'm on my own here.

I'm extremely surprised that I can't connect ubuntu to a standard DHCP network and be able to reliably see my computer name from other machines on that network. Not having read your links yet, is that really what you are saying? That what I want is fundamentally impossible?

---

### Post by bodhi.zazen on 2011-08-18
> **paxxus said:**
> Thanks bodhi, I will study the links you gave.

To give a little background, my office have externally hired IT support costing an arm and a leg. My office desktop came with Windows installed and that's what is supported. I can't really expect to get support for my own ubuntu hacking and demand all kinds of special router setup just for me when everybody else can use the default DHCP setup. It's already borderline that I'm dual booting ubuntu. In other words, I'm on my own here.

I'm extremely surprised that I can't connect ubuntu to a standard DHCP network and be able to reliably see my computer name from other machines on that network. Not having read your links yet, is that really what you are saying? That what I want is fundamentally impossible?

The old adage - Linux is not windows applies.

Windows machines make all kinds of noise on the network, see winns

[http://en.wikipedia.org/wiki/Windows_Internet_Name_Service](http://en.wikipedia.org/wiki/Windows_Internet_Name_Service)

As well as the samba link I gave you.

Your problem is that you are not the network sysadmin and linux uses other solutions.

You can look at Avahi

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

---

### Post by Morbius1 on 2011-08-18
> I'm extremely surprised that I can't connect ubuntu to a standard DHCP  network and be able to reliably see my computer name from other machines  on that network. Not having read your links yet, is that really what  you are saying? That what I want is fundamentally impossible?But you can do all those things:
> I'm running ubuntu 10.04 and what I see is that after a few days up-time  other computers on our LAN cannot resolve my ubuntu name anymore.The problem and what the folks here are trying to resolve is that after >48 hrs or so your machine disappears from the network.

You'll have to admit that's an odd problem.

---

### Post by bodhi.zazen on 2011-08-18
> **Morbius1 said:**
> You'll have to admit that's an odd problem.

I believe it is a problem with the router asit assume the router is doing the DNS.

After the router DNS fails, the windows machines announce themselves, the Ubuntu machine does not.

Hard to debug as an end user without admin access to the network.

---

### Post by paxxus on 2011-08-18
Is there a command that I can issue which causes the Ubuntu to announce itself? I'm thinking that I could make a cron job which does that each night or something thereby presumably re-arming the timer in the router.

I tried "sudo dhclient eth0", but that was a little too brutal since I lost my connections (ssh logins etc.), which is no good. I need this Ubuntu machine to be operational 24/7.

---

### Post by bodhi.zazen on 2011-08-18
Avahi

---

### Post by paxxus on 2011-08-18
Got it ;)

---

### Post by paxxus on 2011-08-19
Avahi is already running as default on ubuntu 10.04. I went through the options and although many of them means nothing to me the defaults seem ok.

Anyway, I have changed /etc/avahi/avahi-daemon.conf to define the host-name and domain-name options, although I can't see that this should be needed. The rest of the options I have left unchanged as I really have no idea what to do with those.

Additionally I have updated /etc/dhcp3/dhclient.conf to define the actual hostname with the "send host-name" option. Furthermore I have removed the host-name option from the request list (since I'm supplying the host-name, not requesting it from the DNS server). I also set the dhcp-lease-time to 3600 for what it's worth.

I must admit that I have very little hope that any of this will work since I basically don't know what I'm doing here.

I will now let it run for some days, perhaps a week, and report back. Any additional suggestions are of course very welcome.

---

### Post by bodhi.zazen on 2011-08-19
See:

[http://avahi.org/wiki/Avah4users](http://avahi.org/wiki/Avah4users) - #11 in particular

And

[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

In my experience, avahi does not seem to work the way it should and I have difficulty pinging hostname.local 

IMO it is easier to add a dns service on my LAN, ask you network admin for assistance if avahi does not work.

---

### Post by paxxus on 2011-08-19
@bodhi: I don't think that the .local stuff applies to me as my domain is company.com.

Regarding a DNS service, I think it is already there on the LAN. I managed to use the nsupdate command to create an alias for my ubuntu - after that I could ping my ubuntu from other servers using foo.company.com or just foo ("foo" was the alias I created).

---

### Post by bodhi.zazen on 2011-08-19
Sounds like you have a solution (DNS) which would be my #1-10 top choices.

.local is used by avahi:

```
ping oneiric.local -c1
PING oneiric.local (**192.168.1.5**) 56(84) bytes of data.
64 bytes from oneiric.local (**192.168.1.5**): icmp_req=1 ttl=64 time=0.251 ms
```

See how I can ping using oneiric.local ? see how the ip address is on my lan ?

The "problem" is avahi is not configured "out of the box"

Once it is, you can then ping, ssh, samba, nfs, etc using hostname.local without a dns server or adding the server to your hosts file.

It is sort of a hack and thus, IMO, a dns server is preferred.

---

### Post by paxxus on 2011-08-19
> **bodhi.zazen said:**
> See how I can ping using oneiric.local ? see how the ip address is on my lan ?
I'm afraid that my noobdom prevents me from understanding what it is I should notice :D

---

### Post by bodhi.zazen on 2011-08-19
When you ping a machine, you ping by hostname

ping hostname

DNS translates "hostname" to an ipaddress.

avahi acts as a dns server, but it appends the hostname, buy default, with .local

so 

ping hostname.local

likewise, rather then ssh hostname, ssh hostname.local

and for your nfs shares you append .local to the hostname.

See the links I gave you for details.

---

### Post by paxxus on 2011-08-25
I ran over the weekend with the various configuration file edits I mentioned, but it didn''t work - my ubuntu was "forgotten" monday morning and I had to reboot. I therefore reverted the Avahi and DHCP configuration files to the installation defaults.

Instead I made a little script which renews the DNS entry via the nsupdate command and I run this script every minute through a cron job. This actually seems to work in that my ubuntu no longer seems to be forgotten by the other servers on the LAN.

But alas, my NFS mounts still failed ("Permission denied") after the usual 2-3 days despite that my ubuntu machine name could now be resolved (thanks to my script) by the NFS server.

Would a fixed IP setup fix this (remember, my DHCP IP address never changes, but it might of course be renewed)? Does a DHCP renew event cause the NFS mounts to fail even if you get the same IP again (which I do)?

---

### Post by paxxus on 2011-08-25
Let me add that I have multiple ssh sessions going when this happens, and they are not affected by the NFS failure. I have tried to manually unmount and remount the NFS shates, but I still get "permission denied", only a reboot fixes the problem - for few days :(

---

