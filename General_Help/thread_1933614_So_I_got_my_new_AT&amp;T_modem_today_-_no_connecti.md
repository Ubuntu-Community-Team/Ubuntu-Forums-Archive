---
title: "So I got my new AT&amp;T modem today - no connection"
date: 2012-02-29
forum: General Help
---

### Post by imachavel on 2012-02-29
Scenario: 2 computers

Pc2-pc: windows 7, it seems that windows 7 couldn't reconnect, as it released the NIC driver when I restarted(blows huh?)

Dimension 4700: Ubuntu 11.04 OS, no connection either, but I need that windows 7 driver to exist on a flash drive, I need to look for says mobo NIC driver. I can log in to AT&T modem, with 192.168.1.254, standard you all know the drill. In network in system settings in top left icon(I'm using unity interface), shows network connection, if config looks standard. Ping google nada. Trace route nada any I.p. nada. Ping 127.0.0.1 get 4 64 byte returns all over the place. So it's weird when I log in to that 2wire it must not be configured but I configured it and it says it connected, the model is net gear adsl2 router, I believe, I'm looking on the bottom. Also strange windows 7 can ping loop back as well.

Dhclient - r and then dhclient seem to change nothing. I was reading this also:

[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

Anyway any suggestions? I'll type anything into Linux terminal that will give good results, be kind I am on an iPad I can't copy paste so will have to type it all out manually :crying:

---

### Post by imachavel on 2012-02-29
Ok, I had to call AT&T, obviously they need to give you a user name and password, the one within the modem is generic. I re logged in with correct user account information, am about to re trouble shoot. If nothin works I'll reply here and go through the steps again, once again, any advice would be appreciated.

---

### Post by imachavel on 2012-02-29
I can connect wirelessly to the modem, it looks as though it might actually be a driver issue on both pcs, as usually wireless goes before a hard wired connection does. I'm still not great at reading lsmod, i'm going I try booting the live cd and seeing if I can connect, if so I'll grab a windows NIC driver, and also I suppose I'll look for a driver that will work for my dell and windows kernel. If not I'll try and grab a windows NIC driver and install it through restricted drivers. The do updates on both pcs if connection occurs.

I suppose I could also try using the Linux mint partition I have on dell hdd. No that doesn't seem to work. Has anyone before heard of a modem that won't give a hard wired connection but will give a wireless ssid?

---

### Post by efflandt on 2012-02-29
What brand/model modem, and is it for DSL or Uverse (or mobile data?).  In any case if it is for DSL or Uverse, it is usually actually a modem/router, but unless it has multiple ethernet LAN ports, it might only give out one private LAN IP.  And assuming you could get a nic to work on any computer, trying to initially go anywhere with a web browser should take you to the setup wizard for the modem/router (not sure if that requires java).

If it is a 2Wire, by default wireless is enabled and default WEP key is typically in square brackets [ ] on the modem label.

---

### Post by imachavel on 2012-02-29
It's got Ethernet ports, I mentioned hard wired. It's a net gear adsl2+ router configured with AT&T software, log in to 192.168.1.254 works, come to think of it, with a bad driver this wouldn't work right? Without a driver there would be no network adapter interface connection at all. Wtf then it's gotta be a modem issue, having problems with the live cd. Man I'm an idiot what is wrong with me.

Should I call back AT&T support? I think I got confused when loop back ping worked for both pcs. Come to think of it, that requires driver installation as well. Lol so windows 7 should have a working NIC driver. Wtf otherwise how would ping 127.0.0.1 work??? God I'm kind of dull at times. Well.......... Call back AT&T? We did a hard reset and everything.

---

### Post by imachavel on 2012-02-29
Hello if I try a dhclient - r, then try a dhclient, and get the answer: RTNETLINK answers, what does that mean?

I can't boot to my live cd for some reason, going to try it on another machine

---

### Post by imachavel on 2012-02-29
Ok me again, sorry to keep bumping this thread. Something is wrong, I've given up trying to boot o the live cd, simply because it isn't working for some reason. I think something is wrong with the modem configuration. I can hard wired connect to ip address 192.168.1.254 just fine. I can get in the settings. The modem has to be configured incorrectly. Even wirelessly I'm getting kicked off quite often. If I had no connection/driver/configuration, why would I be able to log in to the modem. I am trying to figure out how to wipe out my ip information and get new info, dhclientn- r isn't doing it, restarting the computer isn't doing it. I MUST be that the modem isn't wanting any ip addresses to route to the DNS server. I can't think of too much more info I could post, how about this:

Dmesg | Greg eth
[ 5.870942] e100 0000:03:08.0: eth0: address 

Eh I'm not going to type it all out, the Mac address: 00:13:20:37:87:1b

Eth0: NIC link is up 100 Mbps full duplex
ADDCONF(NETDEV_CHANGE): eth0: link becomes ready

Any of that help?

Crap, maybe I SHOULD get back on the phone with AT&T

---

### Post by jerome1232 on 2012-02-29
Out of curiosity is the modem even getting adsl sync? Does it have status lights on it? If so what are they, colors and labels. You said you can get to the config page of the modem, think you could slap a screen-shot of it up?

Are you positive your getting pppoe auth? (your username and password are correct as they are stored in the modem?)

edit: If you can get to the config page of the modem, then in all likelihood this is an AT&T issue, not a you issue.

Can you post the output of ```
ifconfig | grep "inet addr:"
```

---

### Post by efflandt on 2012-03-01
In Windows in a command window see if **ipconfig /all** shows an IP address, gateway, and nameserver(s), which would likely be same as the gateway.  How would you end up with a Win7 PC that you think did not include working network drivers?

In Linux check the output of **ifconfig -a** for an IP address, **route -n** for a default gateway (UG with zeros for Destination and Genmask), and **cat /etc/resolv.conf** for nameserver(s).

127.0.0.1 is loopback (yourself), so if networking is up that is always there, whether any network interface is working or not.

What network device does your Dell have that makes you think it needs a Windows driver in Linux.  What is the output of **sudo lspci -v** related to it?

You still have not said what specific model modem.  But pretty standard, are DSL light (sync) and Internet (PPPoE connected) both solid green?  If the first is not solid green (no sync), you will not get the latter.  And if just the latter is not solid green, check the username (full e-mail address including domain) and password are set correctly on the modem for PPPoE.  Somewhere in its config, I would think that the modem would show upload/download connection speed if it has sync and public IP address if PPPoE is successful.

Is this new service or replacement for a failed modem?  If it is new service or you moved, maybe there is no DSL signal yet.

---

### Post by imachavel on 2012-03-01
No you don't understand, 2 computers, one with one windows 7, one with Ubuntu 11.04
As you said connecting 11.4 Ubuntu to the router is not difficult, I think only windows 7 has the driver issue. Now as per request:

Green lights for power and 1 2 3 ports as well as
Wireless broadband and service. No green light for wps, I suppose I should configure that but first I'd like to establish all healthy connection. I was currently connected through wi fi on this pc, but the connection dropped. I have noticed inside the modem settings connection. Check results:

Ethernet pass
Dsl pass
ATM pass
Pppoe
Authentication
Ip
DNs

All pass, now for host results as per request

If config | grep "inet addr:"
Inet addr: 192.168.0100    Blast:192.168.0.255 mask:255.255.255.0
Inet addr: 127.0.0.1 mask:255.0.0.0
Inet addr: 192.168.1.66. Bcast:192.168.1.255 mask:255.255.255.0

Ifconfig ip address is 192.168.0.100 and that's not a dhcp address

Route - n default gateway:

192.168.0.1

Here is the problem, that's the ip config of my previous d link router which is trying to give me dhcp, dns address default gateway is what I'm looking for right? I can reconfigure everything to the d link, but I was hoping to do that after an established connection to the AT&T modem. I was hoping dhclient - r would release the information and dhclient would renew it, I guess not. This doesn't explain wireless dropping me but that might be because the AT&T modem is resetting the password for some reason. Which I should fix by calling AT&T support. What is the equivalent of DNs release or netsh winsock reset which are windows commands.

We are getti somewhere, which is better then nothing, last but not least

Cat /etc/resolv.conf. No need to ls the .conf file is def in that folder

# generated by network manager
Name server 192.168.0.1
Name server 192.168.1.254

Same problem, wrong default gateway, thank god I'm not subletting here, the 192.168. Address range makes no need for me to figure out 256 - 2 ip addresses, or subnet even further for a cidr. Anyway sorry to get off track, does this cover everything? Any suggestions would be much appreciated

---

### Post by imachavel on 2012-03-01
Sudo /etc/init.d/networking restart

Sudo /etc/init.d/networking start

Sudo /etc/init.d/networking stop

Tried them all, same result. No Internet connection. But once again, I can log into the router. I'm thinking I'll call back AT&T. It sucks though because they say they don't support Linux, but windows 7 has no installed driver for NIC:confused:

Well, no the network service didn't restart, at least not completely. Route - n shows the same 192.168.0.1

Well, wtf. Maybe the new neat gear has the same default ip address. Shut down both computers, remove Ethernet, this should force a renewed network to pull new ips correct??

---

### Post by jerome1232 on 2012-03-01
Wait, are you using 2 routers here? 2wire gateways are router/modem combo's, if you also have a netgear router connected that may be what's causing your problems.

That output of route is showing 192.168.0.1, but a 2wire by default uses 192.168.1.254 (or in your case 192.168.0.254, seems odd yours is using that network but w/e)

What I'm saying is you need to disconnect the netgear and everything should work.

edit:perhaps I'm missing something, are you trying to turn the 2wire into a dumb modem and use the netgear as a router? Is this standard dsl or Uverse?

---

### Post by imachavel on 2012-03-01
oh right LOL!! HAAAA!!!! DUDE IM SO STUPID

yes disconnected the seperate router, just using the at&t 750 modem now. OH wow I'm stupid!! Hahaha!! I owe you a case of beers my man, thank god I can now surf the web using Ubuntu 11.04 and pull up pages at the same time while using apps. I guess I'm spoiled, wasn't too hard to do that using the ipad and just typing everything out, but copy and paste is SO easy! How do I change the status to solved??

---

### Post by jerome1232 on 2012-03-01
> **imachavel said:**
> How do I change the status to solved??

Thread Tools, mark as solved

It's always the small things that evade us :P

---

