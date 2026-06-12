---
title: "Help: Installed Updates now wired connection no longer works"
date: 2012-08-30
forum: General Help
---

### Post by JC24 on 2012-08-30
version: 10.04
 
my wife's uses this computer solely for checking emails / light internet use. She regularly does the recommended updates. Tonight, she ran the updates and shut off her computer. We logged in later to check her email and it said her Wired connection was disconnected. I know it is not a problem with our ISP because my computer works (obviously, i am posting from it). The ethernet cord going into her computer seems fine too because the lights in the back of the computer at the ethernet port are blinking.
 
i did some searching on this forum and found this thread:
[http://ubuntuforums.org/showthread.php?t=2050057&highlight=wired](http://ubuntuforums.org/showthread.php?t=2050057&highlight=wired)
 
I then check my own: cat /etc/network/interfaces
and it said:
 
auto lo
iface lo inet loopback
 
 
Just based on that thread I changed it to read:
 
auto lo
iface lo inet loopback
auto eth0 
 
but it still doesnt work.
 
EDIT*** : i restated my wife's computer and now it doesnt even search for the wired connection (before it would search for a little bit and then say "disconnected" ... Now when I open up "Network Connections" under the Wired tab there is nothing. Previously there was 1 entry ... i dont remember exactly what it said but i think it said auto eth0, late used "never")
 
 
 
Any sugesstions?
Thank you!

---

### Post by JC24 on 2012-08-31
if it helps any, this is what i get from ifconfig -a :
 
eth0
Link encap: Ethernet HWaddr 40:60:87:06:55:db
inet6 addr: fe80::4621:87gg:fe06:55db/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX Packets: 153 Errors: 0 Dropped: 0 overruns:0 frame:0
TX packets: 13 errors: 0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
rx bytes: 40253 (40.2kb) TX bytes: 2914 (2.9kb)
Interrupt:27 Base address:0x4000
 
lo
Link encap:local loopback
inet addr: 127.0.0.1 mask: 255.0.0.0
inet6addr: ::1/128 scope:Host
UP Loopback Running MTU: 16436 Metric:1
RX Packets: 89 Errors: 0 Dropped: 0 overruns:0 frame:0
TX packets: 89 errors: 0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
rx bytes: 10207 (10.2kb) TX bytes: 10207 (10.2kb)

---

