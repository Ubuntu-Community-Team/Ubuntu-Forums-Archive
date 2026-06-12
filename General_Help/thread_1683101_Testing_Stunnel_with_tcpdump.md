---
title: "Testing Stunnel with tcpdump"
date: 2011-02-07
forum: General Help
---

### Post by shad0wman on 2011-02-07
i have setup stunnel between two systems and have syslogs sent from the client to the server.

i would like to test stunnel (whether it's encrypting or not) but i'm not sure if i'm doing the test right, therefore i hope someone can help me check if i'm doing the right thing.

basically, i'm using tcpdump (since i can't use wireshark for corporate security reasons) to test whether any cleartext is seen when client transmits a message to server.

at the client side, i ran the following:
```
root@VMClient2:/etc/rsyslog.d# logger this is a test from client to server
```and below is the output of my tcpdump on the server side:

```
root@VMServer2:/etc/rsyslog.d# tcpdump src 10.188.77.108 and dst 10.188.77.174
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
14:50:44.815113 IP VMClient2.local.35453 > VMServer2.local.60514: Flags [P.], seq 3402676368:3402676490, ack 3385933259, win 241, options [nop,nop,TS val 989804 ecr 969104], length 122
14:50:49.815474 ARP, Reply VMClient2.local is-at 08:00:27:5e:dc:a4 (oui Unknown), length 46

```am i doing the testing right? hope someone can help. thanks!

---

