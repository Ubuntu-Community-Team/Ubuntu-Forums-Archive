---
title: "very slow internet in Ubuntu 10.04 - Compaq Prescario cq60 (amd 64bit)"
date: 2010-05-13
forum: General Help
---

### Post by aske on 2010-05-13
Hello,

I am quite new to ubuntu, so after searching since last night i would appreciate some help...

My internet is slow (which was not when i had tried the 9.10 version) and a couple of solutions i tried did not end up helping me.
first of all i tried this:
sudo ethtool -s eth0 speed 100 duplex full autoneg on
found here: [http://ubuntuforums.org/showthread.php?t=1395866](http://ubuntuforums.org/showthread.php?t=1395866)
no help :(

second, I tried this: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)  - no help again :(

third, i tried this: [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10) - no help.

fourth, i tried again the second :)

lastly, which seemed very promising, was this:
[http://ubuntuforums.org/showthread.php?t=1434732&page=2](http://ubuntuforums.org/showthread.php?t=1434732&page=2) - shortly the 
"sudo pppoeconf" command. at this point, i get this error:

Sorry, I scanned 2 interfaces, but the Access            &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem. 

...for which i could not find a solution...

i appreciate any help,

Thanx,
Anthony

---

### Post by aske on 2010-05-13
Hi again,

i just now checked with Skype, and it seems that the speed is much better than the browsers. a video call worked like a charm, and the download speed of an mp3 file was from 50 to 75 kbps, which is more or less the average speed i always experienced in skype..

another update: i disabled the ipv6 in firefox also (apart from disabling it in my system generally) - nothing.
the same download speed is both in firefox and chrome.

hope someone could give me a hint of what is going on..

thanx again,
anthony

---

### Post by ThaddeusW on 2010-05-13
Firefox is the only "slow" application? Are you using any kind of proxy for web browsing?

Even if you Ethernet card was stuck at 10Mbps you should be able to get maximum speeds of 800+ KBps assuming you internet connection could handle it.

If you want to check the link speed of your Ethernet card type:
```
dmesg |grep eth0
```
Your Ethernet card should be eth0 if its the only adapter in the system.

If you have another computer on the same network try running a speed test on it and compare the results to a speed test on your Ubuntu machine.

---

### Post by aske on 2010-05-13
thanx for the reply.

i ran the command and this is the result
```
[    1.351276] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:16:d7:2f:b2

```

(which i don't know what exactly means..)

firefox and chrome have the same exact behavior.

i have already tested with linux mint 8 in another computer and the speed is indeed faster - as it should normally be.

---

### Post by ThaddeusW on 2010-05-13
Your dmesg should look like this.
```

[    6.083607] sky2 eth0: addr 00:e0:4d:75:c8:25
[   20.468764] sky2 eth0: enabling interface
[   20.468972] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.325856] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.326046] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.984513] eth0: no IPv6 routers present

```

As you can see, the line that says "*sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx*" shows you the link speed.

---

### Post by aske on 2010-05-13
> **ThaddeusW said:**
> Your dmesg should look like this.
```

[    6.083607] sky2 eth0: addr 00:e0:4d:75:c8:25
[   20.468764] sky2 eth0: enabling interface
[   20.468972] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.325856] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.326046] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.984513] eth0: no IPv6 routers present

```

As you can see, the line that says "*sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx*" shows you the link speed.
Thanks!

But do you know a way to fix this? How is this related to my original problem?

---

### Post by aske on 2010-05-13
> **ThaddeusW said:**
> Your dmesg should look like this.
```

[    6.083607] sky2 eth0: addr 00:e0:4d:75:c8:25
[   20.468764] sky2 eth0: enabling interface
[   20.468972] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.325856] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.326046] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.984513] eth0: no IPv6 routers present

```

As you can see, the line that says "*sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx*" shows you the link speed.
Thanks!

But do you know a way to fix this? How is this related to my original problem?

---

### Post by aske on 2010-05-13
...is there anyone that could give me a hint of what else i should try? i have been still searching for that error in the "sudo pppoeconf" which seems to be the solution to the problem but i cannot find anything..

thanx..

---

### Post by aske on 2010-05-13
hello - again.

i removed the cable and joined a wireless network, and it seems to work better than the wired one..! (although this network was not so strong). so i started thinking about the drivers of my ethernet card..

i am posting this, which i don't know if it will help - i'm posting it anyway:
```
anthony@anthony-laptop:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:d7:2f:b2
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:66:71:8b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.108 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```

then, for the "product: MCP77 Ethernet" device i found this link:
[http://manpages.ubuntu.com/manpages/lucid/man4/if_nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/if_nfe.4freebsd.html)
which again i don't know if it is of any help. anyway, i could not figure out what to do and how to do it to install this driver to my machine - or if i should do it.

please, PLEASE, let me know, something, anything that you might need, or anywhere that i could search to get me somewhere, i have been fighting for two days now and i am desperate..

thanx,
anthony

---

### Post by aske on 2010-10-24
Hello,

after so much time, there is an update.
all these months it just did not happen to have to use my cable to connect to the internet - i connected always through wireless. but now i need to connect through cable - and i found that here is the problem.

when connecting through ethernet, internet is REALLY slow. i was downloading from the repos now with less than 10kbps - whereas my normal connection speed would exceed the 200 for sure.

SO:
wireless - no problem.
ethernet - no internet :p

info about what i have tried (it is the same configurations still, haven't touched anything) and what my hardware etc are - see above.

Any ideas on what i should try?

thanx.

---

### Post by aske on 2010-10-26
Hello again,

it seems that in the general help that this post is at the moment i am not getting any help, i got very little some months ago when i started the thread, i got no help now.
can the mods please move it to "networking and internet", it is possible that there i could get a bit more attention.

i cannot use my cable to connect to the internet, and i am using the wireless from a friend which is annoying for both of us, so i am once again asking for your help.

thanx.

---

