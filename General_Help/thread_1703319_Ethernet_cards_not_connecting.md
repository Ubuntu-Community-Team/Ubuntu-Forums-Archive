---
title: "Ethernet cards not connecting"
date: 2011-03-09
forum: General Help
---

### Post by rolljas on 2011-03-09
Hi guys,

i really need some help with this one.

i have ubuntu 10.10 64b and for some reason last night the wired network autoeth01 suddenly will not connect to my router. it is a dual boot machine so i booted into windows and it is working fine in that OS.

I then had a look at the status on my laptop running ubuntu 10.10 32b and that was showing the same message "wired network autoeth01 disconnected" i cannot for the life of me figure this out. just before it was disconnected i had been copying 7gigs worth of data using samba from the 32b machine to the 64 bit machine.

anyone got any suggestion? 

i have tried deleting the wired entry and recreating it. 

tried different cables

even changed the router

works with all windows machines connected to network

i really appreciate any suggestion

here is what comes up in lfconfig:

jason@ubuntu1:~$ lfconfig
No command 'lfconfig' found, did you mean:
 Command 'fconfig' from package 'redboot-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
 Command 'ldconfig' from package 'libc-bin' (main)
lfconfig: command not found
jason@ubuntu1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:b3:68:c9  
          inet6 addr: fe80::226:b9ff:feb3:68c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133319 (133.3 KB)  TX bytes:21926 (21.9 KB)
          Interrupt:22 Memory:f6ae0000-f6b00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:651236 (651.2 KB)  TX bytes:651236 (651.2 KB)

wlan0     Link encap:Ethernet  HWaddr 58:94:6b:8b:99:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dandnsmith on 2011-03-09
Sounds like the problem might be in the router.
Are you configured to use DHCP for automatic allocation of IP address?
If so, what is the allocation time for the address?
Are you trying both machines via the same port on the router?
Did you try re-booting the router?
Have you looked at the IP4 bits on the Ubuntu machine(s) for the eth connection(s)?

---

### Post by rolljas on 2011-03-09
hi Derek,

yes it is configured to use dhcp not sure what the allocation time is as i cant seem to find it. i have rebooted the router.. and even tried it with another netgear switch and a dlink switch its the same using those as well...
 the thing thats got me is that i can booting into windows on all the above devices and they work no problem. 

i haven looked at the IP4 bits on the ubuntu machines as i am not sure how, 

thanks for you reply

---

### Post by dandnsmith on 2011-03-09
To check the IP4 settings: use the System|Preferences|Network Connections,
and the select the connection and 'edit' it. That brings up a window with IP4 Settings and IP6 Settings tabs.

I have mine set to ignore IP6 (because I know my ISP doesn't handle IP6), and have the IP4 set to Manual (historic reasons to do with mixed systems and printers ...). The Manual setting avoids any router induced session/link timeouts (which, to my way of thinking, reduces potential problems).

You'll probably find, if you haven't changed things, that the Windows is using IP4 with DHCP!

I don't really understand your setup - the mention of Netgear and DLink switches makes me wonder if there are any pitfalls there. I do have a router and a hub - not quite as complicated

---

### Post by rolljas on 2011-03-09
yes looking on my ubuntu 32 bit machine it is setup to ignore IP6

yep windows is using ip4 with DHCP.

actually my setup is super simple, i probably just made is sound more complex than it it.

i have four machines, two of them are pure windows machines and the other two are dual boot windows / linux. they all connect via cat5 to my netgear switch and talk to each other from there

i just happen to have some spare routers / switches / hubs sitting around from work that i then tried to use to trouble shoot

i will try setting ip4 to manual and see if that makes any difference

---

### Post by rolljas on 2011-03-09
woo! you rock 

Thanks Derek i didnt think to give it a manual IP. awesome thanks for that :)

that fixed it!

---

### Post by dandnsmith on 2011-03-09
Ok - good luck. Hope that fixes it.

---

