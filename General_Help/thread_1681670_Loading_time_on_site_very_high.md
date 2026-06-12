---
title: "Loading time on site very high"
date: 2011-02-04
forum: General Help
---

### Post by GunniH on 2011-02-04
Hi there,

I just bought a new VPS to host my site, it gets about 120k pageviews per day.

```
top - 21:32:38 up 1 day, 12:33,  2 users,  load average: 0.39, 0.44, 0.41
Tasks: 237 total,   1 running, 236 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us,  0.6%sy,  0.0%ni, 97.5%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:  12324128k total,  3977540k used,  8346588k free,   201892k buffers
Swap:  2102456k total,        0k used,  2102456k free,  2941276k cached
```

Here are the top stats, as you can see the server load is almost nothing but the site takes quite some time to load.

Here is iostat -x:

```
Linux 2.6.32-25-server (srv01.clgaming.net)     02/04/2011      _x86_64_        (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.55    0.00    0.82    0.15    0.00   97.48

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.78    10.37  170.11    6.64 21847.84   134.89   124.37     2.06   11.65   0.74  13.05
sdb               0.08    10.99    0.05  176.69     1.62 21980.59   124.38     4.82   27.30   1.04  18.36
md0               0.00     0.00    0.00    0.00     0.01     0.00     8.00     0.00    0.00   0.00   0.00
md1               0.00     0.00    0.00    0.21     0.00     0.42     2.01     0.00    0.00   0.00   0.00
md2               0.00     0.00    0.10   16.38     3.29   131.03     8.15     0.00    0.00   0.00   0.00

```

And at last netstat -s

```
Ip:
    15442728 total packets received
    0 forwarded
    0 incoming packets discarded
    15442722 incoming packets delivered
    21105836 requests sent out
    3 fragments dropped after timeout
    6 reassemblies required
    3 packet reassembles failed
Icmp:
    6387 ICMP messages received
    5615 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 495
        timeout in transit: 32
        redirects: 141
        echo requests: 100
        echo replies: 4
    691 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 591
        echo replies: 100
IcmpMsg:
        InType0: 4
        InType3: 495
        InType5: 141
        InType8: 100
        InType11: 32
        OutType0: 100
        OutType3: 591
Tcp:
    130731 active connections openings
    769399 passive connection openings
    13840 failed connection attempts
    13096 connection resets received
    258 connections established
    15147726 segments received
    20591423 segments send out
    225863 segments retransmited
    46 bad segments received.
    27018 resets sent
Udp:
    287838 packets received
    608 packets to unknown port received.
    0 packet receive errors
    287859 packets sent
UdpLite:
TcpExt:
    24490 invalid SYN cookies received
    13097 resets received for embryonic SYN_RECV sockets
    1 packets pruned from receive queue because of socket buffer overrun
    5 ICMP packets dropped because they were out-of-window
    577741 TCP sockets finished time wait in fast timer
    1 time wait sockets recycled by time stamp
    50 packets rejects in established connections because of timestamp
    48445 delayed acks sent
    52 delayed acks further delayed because of locked socket
    Quick ack mode was activated 10534 times
    144157 times the listen queue of a socket overflowed
    144157 SYNs to LISTEN sockets dropped
    3658 packets directly queued to recvmsg prequeue.
    501 bytes directly received in process context from prequeue
    1022616 packet headers predicted
    5 packets header predicted and directly queued to user
    4425390 acknowledgments not containing data payload received
    5058734 predicted acknowledgments
    360 times recovered from packet loss due to fast retransmit
    44064 times recovered from packet loss by selective acknowledgements
    206 bad SACK blocks received
    Detected reordering 210 times using FACK
    Detected reordering 146 times using SACK
    Detected reordering 51 times using reno fast retransmit
    Detected reordering 97 times using time stamp
    131 congestion windows fully recovered without slow start
    781 congestion windows partially recovered using Hoe heuristic
    13683 congestion windows recovered without slow start by DSACK
    1563 congestion windows recovered without slow start after partial ack
    46796 TCP data loss events
    TCPLostRetransmit: 2368
    134 timeouts after reno fast retransmit
    5574 timeouts after SACK recovery
    1085 timeouts in loss state
    124846 fast retransmits
    5492 forward retransmits
    32757 retransmits in slow start
    39958 other TCP timeouts
    200 classic Reno fast retransmits failed
    2679 SACK retransmits failed
    65 packets collapsed in receive queue due to low socket buffer
    10547 DSACKs sent for old packets
    8 DSACKs sent for out of order packets
    49250 DSACKs received
    79 DSACKs for out of order packets received
    119 connections reset due to unexpected data
    418 connections reset due to early user close
    1833 connections aborted due to timeout
    TCPSACKDiscard: 109
    TCPDSACKIgnoredOld: 10283
    TCPDSACKIgnoredNoUndo: 3103
    TCPSpuriousRTOs: 635
    TCPSackShiftFallback: 486163
IpExt:
    InBcastPkts: 162
    InOctets: -1125721178
    OutOctets: 1728254501
    InBcastOctets: 53136

```

It sometimes times out and sometimes just takes some time to load.

The server is on a 100mbit connection and it should have no issues running this site.

It was a fresh Ubuntu 10.04 LTS install about 1 and a half day ago, included ispcp (which installed apache, mysql and php).

I figure this is either a network issue or an apache config issue.

Got any protips?

Thanks,
~Gunni

---

### Post by Habitual on 2011-02-06
How many other VPSs are on the same node? *This is NOT your VPS* but the root-node VPS (ask your hosting provider)

How many other domains on *your* VPS?
srv01.clgaming.net resolves to 46.4.69.174.

2 sites on that IP. That's good.

It may be your local network and not the server itself.
since you indicated the server has iostat installed, check sar too and look for a high value in %iowait and a low value in %idle
if you find a time that iowait is high AND idle is low, your system was in trouble during that period.
```
sar | less
```

check the apache access.log for an excessive amount of traffic from a single IP.

Check /var/log/secure for failed login attempts.
It could be bad coding for the webpages at clgaming.net or the caching of 18 Livestreams advertised on your site.

It could be a LOT of things.

**It may be your local network and not the server itself.**
Try a traceroute from your location using 
```
traceroute 46.4.69.174
traceroute clgaming.net
```
in a terminal.

and post the results of the traceroutes here.
I am subscribed to this thread.

---

