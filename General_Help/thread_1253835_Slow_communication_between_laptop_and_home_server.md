---
title: "Slow communication between laptop and home server"
date: 2009-08-30
forum: General Help
---

### Post by bonfire89 on 2009-08-30
Hey there,

This is going to be a pretty high level question since I don't know what is going on. And whatever is going on is subtle.

I currently work on a Jaunty laptop that is sometimes connected to my home LAN on wirelessly and sometimes wired. I have a lot of media content that is off loaded on to a headless media server running ubuntu jaunty server.

The communication between the two has noticeably slowed. Streaming mp3s will often stall. Exaile will crash, other programs connecting to the server will crash and run slow.

Even when I SSH to the server things can slow down, even a simple "ls" on a small folder could take 40 seconds sometimes.

All while network traffic and cpu or memory usage on either end is minimal.



On the server side I have a total of 6 hard drives. 5 of them sit in an LVM. The operating system is not in the LVM. The 6th was added recently and is part of the LVM. During the install I ran into issues of the drive not registering at all and registering with incorrect size values. I determined it was a power issue and upgraded the PSU by a couple hundred watts.

CPU is running at the same temperature as usual.

at least two of the newer hard drives are the Western Digital green drives.

Much of the hardware is about 8 years old.. The days of P4 3.0ghz hyperthreaded.

I believe this issue predates the latest additional hard drive, but maybe not. Actually. I'm really not sure.



I'm looking for suggestions, advice, diagnostic tools anything that *may* help as I realize this question is a bit obscure.

Thanks!



More details

My massive multi terabyte lvm is mounted as /home

The server can be really slow to serve up my web based torrent client (deluge) along with my web based newserver client (sabnzbdplus), **however, I just did a page refresh of duluge while running "top" on the server and it took up all the cpu!**

---

### Post by cariboo on 2009-08-30
Iperf is a command line tool which allows you to check network bandwidth between your laptop and server. Install iperf, it is in the repositories, on your server and you laptop. run iperf on the server by typing:

```
iperf -s
```

This will start iperf in server mode. Then open a terminal on your laptop and type:

```
iperf -c <server>
```

where <server> is your server name or ip address. You should get a result that looks something like this:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.225 port 56744 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.4 Mbits/sec
```

As you can see my transfer rate is 94.4 Mbps, which is acceptable on a 100Mbps network.

---

### Post by bonfire89 on 2009-08-30
Hey, neat tool! I didn't find anything wrong, but, at least I know not to blame the networking aspects

```

iperf -c dude
------------------------------------------------------------
Client connecting to dude, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.138 port 57989 connected with 192.168.1.146 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    112 MBytes  93.7 Mbits/sec

```



I think soon I will try not mounting the lvm and see how things go... something I had previously not thought of.

Part of the problem is that the problem is not consistent.. just a couple times an hour it will really lag on pretty simple tasks.


Thanks! That tool will be useful to know about in the future regardless.

---

### Post by bonfire89 on 2009-08-30
would there be any use running that tool for an hour?




Also note. My massive multi terabyte lvm is mounted as /home

---

