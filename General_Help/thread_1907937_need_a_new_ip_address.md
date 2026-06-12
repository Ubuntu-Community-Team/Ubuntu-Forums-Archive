---
title: "need a new ip address"
date: 2012-01-12
forum: General Help
---

### Post by **dyani** on 2012-01-12
Hello Ubuntu users
I realize that many people prefer to have static ip addresses, but I really want a dynamic one. I can't even get a new ip.I have tried many of the suggestions that I have found in forums but nothing works, or when it does I have no Internet connection. It seems that my system has somehow become permanently locked to this static ip

---

### Post by 0011235813 on 2012-01-12
> ****dyani** said:**
> Hello Ubuntu users
I realize that many people prefer to have static ip addresses, but I really want a dynamic one. I can't even get a new ip.I have tried many of the suggestions that I have found in forums but nothing works, or when it does I have no Internet connection. It seems that my system has somehow become permanently locked to this static ip

Why don't you try tor proxy? It works reasonably fast, and it uses a number of different IP addresses. Use the following: ```
sudo apt-get install tor
``` and then configure your clients to use it. You can download FoxyProxy add-on for Firefox& Thunderbird and right click-tor wizard. Tor should run automatically, but if it isn't you can use:
```
tor
``` in the terminal. You can configure tor in other browsers like Opera in preferences, but they must support SOCKS proxy. Type the following in the SOCKS proxy bar:

IP address: 127.0.0.1  Port: 9050

---

### Post by **dyani** on 2012-01-12
[QUOTE=0011235813;11605816]Why don't you try tor proxy? It works reasonably fast, and it uses a number of different IP addresses. Use the following: ```
sudo apt-get install tor
``` and then configure your clients to use it. You can download FoxyProxy add-on for Firefox& Thunderbird and right click-tor wizard. Tor should run automatically, but if it isn't you can use:
```
tor
``` in the terminal. You can configure tor in other browsers like Opera in preferences, but they must support SOCKS proxy. Type the following in the SOCKS proxy bar:

IP address: 127.0.0.1  Port: 9050[/QUOTE

thanks for the suggestion. Although the proxy sounds like a good idea, I still need a new ip since my firewall gets attacks sometimes even before I open the browser. I am a bit mystified at how my ip address just became static on its own..

---

### Post by lisati on 2012-01-12
Is this an IP address on your local network, or your public IP address? How is the IP address assigned - through a setting in your modem/router or through a setting you have made on your Ubuntu box?

If you're talking about your public IP address, take a look here: [http://whatismyipaddress.com/change-ip](http://whatismyipaddress.com/change-ip)

---

### Post by **dyani** on 2012-01-12
> **lisati said:**
> Is this an IP address on your local network, or your public IP address? How is the IP address assigned - through a setting in your modem/router or through a setting you have made on your Ubuntu box?

If you're talking about your public IP address, take a look here: [http://whatismyipaddress.com/change-ip](http://whatismyipaddress.com/change-ip)

it is my public ip address on  a stand alone computer.It used the default configurations from the Ubuntu installation, and somehow it became a fixed one. I have tried many of the suggestions that I found in forums for other people who had the same issue, including editing   /etc/network/interfaces, var/lib/dhcp3/dhclient,  /var/lib/dhcp3/dhclient.leases,
 /etc/dhcp3/dhclient.conf
When ever the change persists through a restart i have no connection

---

### Post by 0011235813 on 2012-01-12
> ****dyani** said:**
> it is my public ip address on  a stand alone computer.It used the default configurations from the Ubuntu installation, and somehow it became a fixed one. I have tried many of the suggestions that I found in forums for other people who had the same issue, including editing   /etc/network/interfaces, var/lib/dhcp3/dhclient,  /var/lib/dhcp3/dhclient.leases,
 /etc/dhcp3/dhclient.conf
When ever the change persists through a restart i have no connection

I think you should be careful with the firewall. If you're firewall is getting attacked, then you *MIGHT* be able to trace the attackers IP and configure proxy to block it. I also think you should consider the possibility that you may have "fireware" installed- an application that deliberatively attempts to break your firewall- has your system been compromised by any chance? I would also consider any BitTorrent programs you may have installed- they are by definition, insecure- they even bypass your settings if you configure them to use tor.

---

### Post by **dyani** on 2012-01-12
> **0011235813 said:**
> I think you should be careful with the firewall. If you're firewall is getting attacked, then you *MIGHT* be able to trace the attackers IP and configure proxy to block it. I also think you should consider the possibility that you may have "fireware" installed- an application that deliberatively attempts to break your firewall- has your system been compromised by any chance? I would also consider any BitTorrent programs you may have installed- they are by definition, insecure- they even bypass your settings if you configure them to use tor.
  
I have added all ip addresses that repeatedly attack my firewall to the Firestarter deny connections to host list. I have used qBittorrent in the past, but although it is installed on this partition I have not used it.
I have, in a moment of paranoia, wondered if some cracker somehow edited my configuration files to keep me locked into this ip address, but I have seen no real signs of a successful attack

---

### Post by 0011235813 on 2012-01-12
> ****dyani** said:**
> I have added all ip addresses that repeatedly attack my firewall to the Firestarter deny connections to host list. I have used qBittorrent in the past, but although it is installed on this partition I have not used it.
I have, in a moment of paranoia, wondered if some cracker somehow edited my configuration files to keep me locked into this ip address, but I have seen no real signs of a successful attack

Then you may want to contact your ISP and ask them for help. It is possible they may have altered their settings to turn their IP static.

---

### Post by |{urse on 2012-01-12
Reset your router, if your ip changes then it's dynamic, otherwise you'll have to call your isp.

---

### Post by sailor2001 on 2012-01-12
I was always under the impression that only your IP could change you from dynamic to static (extra costs) and vs

---

### Post by **dyani** on 2012-01-12
now i really am mystified. I got tired of the situation and deleted that old partition and did a fresh install and the new one has the same fixed ip address.

I turn off the computer every night and once went away and left it off 4 days, with everything disconnected.
I even took the battery out of the modem for 30 minutes, as instructed by my ISP

I am just wondering now if the default configuration of Ubuntu 10.04 is actually a fixed ip
otherwise I can't see how /var/lib/dhcp3/dhclient would show a fixed ip address in its file

---

### Post by hackertarget on 2012-01-12
Your public IP is assigned by your ISP, it will be either dynamic or static. As suggested try rebooting your router / modem, if that does not work contact your ISP. Some ISP's may give you a dynamic IP but it will stay the same unless you stay disconnected for a certain time period.

In the past I had a "dynamic" IP for nearly two years, that survived a few outages and router restarts.

---

### Post by lisati on 2012-01-12
I'm wondering if unfamiliarity with the way networking works with Ubuntu is causing a bit of confusion here. 

As an example of what I'm thinking of: if you're looking at the output of the ifconfig command, the "inet addr" isn't your public IP address but the one assigned to your computer on your local network. Depending on how your router is configured, it could well give the same IP address. Similarly, the "Bcast addr" is one used on your local network as well, and doesn't usually change.

---

### Post by **dyani** on 2012-01-12
> **lisati said:**
> I'm wondering if unfamiliarity with the way networking works with Ubuntu is causing a bit of confusion here. 

As an example of what I'm thinking of: if you're looking at the output of the ifconfig command, the "inet addr" isn't your public IP address but the one assigned to your computer on your local network. Depending on how your router is configured, it could well give the same IP address. Similarly, the "Bcast addr" is one used on your local network as well, and doesn't usually change.


I am on a standalone computer, not part of a network. I am referring to an  Internet address exactly as it shows on Firestarter which my isp verified for me. It is not a dynamic address that somehow hasn't changed because it is shown in the /var/lib/dhcp3/dhclient file as a fixed address.

---

### Post by 0011235813 on 2012-01-13
I think you should phone up your ISP and ask them to send a technician to fix it. But anyway, using a proxy will act as a temporary solution, and of course, it will give you the advantage of anonymous browsing :) 

If hackers get a proxy IP, they'd be trying to hack into TOR network instead of yours, and good luck to them trying to get in LOL.

---

### Post by hg088 on 2012-01-13
i was banging my head to the wall last week trying get a new ip from the isp's dhcp server.

what worked for me was this script i made:
```
sudo dhclient -r -v eth2 && sudo rm /var/lib/dhcp/*
sleep 1
sudo sh -c "echo 'interface \"eth2\" { send dhcp-requested-address 1.2.3.4;}' >> /etc/dhcp/dhclient.conf"
sleep 1
sudo dhclient -v eth2 &
sleep 1
sudo sed -i '$ d' /etc/dhcp/dhclient.conf
sleep 3
sudo killall dhclient
sleep 6
sudo dhclient -v eth2
```this forces dhclient to ask for an ip different than the one u have assigned (after releasing the current lease of course) through making some changes to the dhclient.conf file. im no pro and this script is probably not the best way to go but it works for me.

after doing some further reading i discovered that the best way to do this is actually changing your mac address. this way your isp's dhcp server will see you as a different computer and assign u a different ip. i belive u should use the package macchanger

---

### Post by efflandt on 2012-01-13
One thing you have not said is what kind of internet connection you have.  If it is cable modem, many ISP's will continue to give you the same automatic IP for a long time (maybe even years).  If it is DSL, the modem is often a modem/router that handles the PPPoE login for the public IP and it gives you a private IP address that may never change if your PC is the only thing on the network.

In any case if your computer is directly connected to the internet with a public IP address, it is going to be constantly probed, and constantly monitoring your firewall logs will make you paranoid, if not drive you insane.  Whether that is any concern at all depends what, if any, uninitiated connections that you allow in through your firewall (things other than replies to what you are connecting to).

---

### Post by lisati on 2012-01-13
> ****dyani** said:**
> I am on a standalone computer, not part of a network. I am referring to an  Internet address exactly as it shows on Firestarter which my isp verified for me. It is not a dynamic address that somehow hasn't changed because it is shown in the /var/lib/dhcp3/dhclient file as a fixed address.

I just had a horrible thought: I think *I* misinterpreted the output of the ifconfig command. :(

(Edit: NVM, it shows the local IP address on my laptop and server as I first thought.)

---

### Post by hg088 on 2012-01-13
hmm, what do you mean lisati?

---

### Post by Slim Odds on 2012-01-13
> **|{urse said:**
> Reset your router, if your ip changes then it's dynamic, otherwise you'll have to call your isp.

That's just not true. Even if you reset your router with a dynamic IP address, you're most likely going to get REASSIGNED the SAME IP address. Most DHCP servers are setup to that they don't just keep changing the addresses frequently for the same machines. They match the MAC address and prefer the old IP address if it's not taken by someone else in the meantime.

---

### Post by lisati on 2012-01-13
> **hg088 said:**
> hmm, what do you mean lisati?

I thought I made a mistake in a previous post. :(

---

