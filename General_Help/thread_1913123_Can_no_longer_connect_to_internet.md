---
title: "Can no longer connect to internet"
date: 2012-01-22
forum: General Help
---

### Post by Nexusx6 on 2012-01-22
I have a server that was up and running two days go, I had made file transfers and edits to a website I have being served from it without problem.

During one session, however, I was SSH'd into the server and was downloading a package when the connect suddenly froze. Mid install of the package the text just stopped moving and neither CTRL+C or CTRL+D even so much as shifted the text upwards, so I killed the terminal session and started a new one, but I couldn't connect anymore. Thinking that the server simply crashed, I physically restarted it, but I still can't connect. I don't see anything wrong during the boot process, the ports on both ends of the cable are lit up (one is orange, I don't remember if that's normal for this motherboard though), all other devices connect to the web fine, and the router sees the server and is assigning it a local IP so I don't know why I can't ping google.com, apt-update fails on every repo, and I cant SSH into the computer even from another computer on the LAN. :confused:

I'd post the result of ifconfig -a, but I can't use pastebin without a connection :/ I'm totally stumped as to why this all happened all of the sudden, any help is greatly appreciated.

---

### Post by NightFoxyarrith on 2012-01-22
Is there any way you can do anything on the server? You could try disabling the firewall
```
 sudo ufw disable 
```
For any further help I will need ifconfig -a though. Maybe a wrong DNS setting? Have you tried pinging an ip adress that's outside your home network? If that doesn't work you can try pinging the router, and if that doesn't work ping 127.0.0.1. Please post any results here, and then I might be able to help you.

---

### Post by Nexusx6 on 2012-01-24
Sorry about the delay, I can get access to the server by going to its physical location and plugging in a monitor and keyboard, but I haven't been able to get to it till today. Thanks for helping.

```
$ ping localhost
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.042 ms

$ ping 192.168.11.1 # Router IP
connect: Network is unreachable

$ ping google.com
ping: unknown host google.com

$ ifconfig eth0 up
$ ifconfig -a

eth0     Link encap:Ethernet HWaddr 00:11:2f:7f:12:62
         inet addr:127.0.0.1 Bcast:192.168.11.255 Mask:255.255.255.0
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:6 errors:0 dropped:0 overruns:0 frame:0
         TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:965 (965.0 B) TX bytes:1340 (1.3 KB)
         Interupt:21 bas address:0xa000

lo       ... #if you need lo, let me know

```

---

### Post by NightFoxyarrith on 2012-01-24
As far as I can see something weird happened. The ip-address for your eth0 is actually the localhost address (127.0.0.1). This won't give you network connectivity, because 127.0.0.1 is reserved for the lo interface (which is the loopback interface to your own machine). You should to a 192.168.11.x ip-address using the ifconfig command
```
sudo ifconfig eth0 add 192.168.11.x netmask 255.255.255.0
```

---

### Post by Nexusx6 on 2012-01-24
Oh hell, I copied that wrong :S I had to hand type that down, and it looks like my eye's drifted to lo when I was typing out the ip address. The actual address is

```
eth0     Link encap:Ethernet HWaddr 00:11:2f:7f:12:62
         inet addr:192.168.11.53 Bcast:192.168.11.255 Mask:255.255.255.0
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:6 errors:0 dropped:0 overruns:0 frame:0
         TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:965 (965.0 B) TX bytes:1340 (1.3 KB)
         Interupt:21 bas address:0xa000
```

192.168.11.53 is the server's lan ip.

---

### Post by NightFoxyarrith on 2012-01-25
Ok, a couple things you could try:
Check the netmask setting in the router, this should be 255.255.255.0. Check if there is a conflicting ip on your network. Try to ping your server from another pc, and then check the arp cache on that pc (even if pinging fails)
```
arp -n
```
Check if the ip from your server gets a MAC address in your arp cache.
Try the same (ping some other host and check the arp cache) on the server.
Maybe try using a different ethernet cable or test the current cable with another computer.
The last one might sound stupid, but I have to make sure you did it, because this often solves tons of network issues, and lots of people don't do it. Try unplugging the router for about 10 seconds and replugging it.

---

### Post by Nexusx6 on 2012-01-26
> Try to ping your server from another pc, and then check the arp cache on that pc (even if pinging fails)
```
arp -n
```
Check if the ip from your server gets a MAC address in your arp cache.
Try the same (ping some other host and check the arp cache) on the server.
Maybe try using a different ethernet cable or test the current cable with another computer.
The last one might sound stupid, but I have to make sure you did it, because this often solves tons of network issues, and lots of people don't do it. Try unplugging the router for about 10 seconds and replugging it.

The netmask checks out

There's no conflicting IP on the router.

arp cache doesn't show the servers IP or MAC address anywhere on the output from the other PC even after I pinged the server from it.

arp -n from the server returns nothing (literally, there's no output to the terminal).

I replaced the cable and cycled the power on the router.

No progress :( I think I'm about ready to reinstall.

---

### Post by NightFoxyarrith on 2012-01-26
I'm out of ideas. Arp might not be working on the server, but I'm not sure. This is the only thing I can think of if the router lists the server IP as active. To check if arp is the problem you can try adding the router ip and mac manually using this command:
```
arp -s 192.168.11.1 00:50:ba:85:85:ca
```
replace the mac address with the actual mac address of your router.
If you can ping the router after that, arp was causing the problem, otherwise I wouldn't know what is wrong. Maybe it's the ethernet port on the router that is broken? Or maybe a cable between the router and pc doesn't work anymore? Reinstalling might work, and if that works we can be sure it wasn't a physical problem, but I'm out of ideas.

---

### Post by Nexusx6 on 2012-01-26
I tried arp -s with my MAC address, but that didn't work either, so I reinstalled everything, and vola, it worked perfectly fine from the first boot up. I got my server restored in just minutes after restoring backups and everything is working great now. 

That was one of the more frustrating issues I've had to wrestle with; I wish I knew what had caused it. Thank you for sticking through the whole thing, I really appreciate posters like you :)

---

