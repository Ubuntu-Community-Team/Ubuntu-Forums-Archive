---
title: "Connection speed is foobared"
date: 2006-03-31
forum: General Help
---

### Post by add1sun on 2006-03-31
I'm on Breezy 5.10 (have been since it released and had this problem all along).  I am connected to a wired router that also has an XP box connected.  Download and browsing on the XP machine is fine and was fine on my old Hoary machine (different machine - now dead).  When I run a bandwidth test, the XP is coming in around 1500-1600Kbps while the Ubuntu is anywhere from 85 - 200Kbps.  Everything about my network connection is slow including browsing, synaptic downloads and LAN (I can't play songs from the windows machine anymore because they lag too much, I have to actually copy them over and then play them locally).

- I have disabled IPv6 with no effect.  
- My DNS is my router (this is how it is on the XP machine too):
addi@ubuntu:~$ cat /etc/resolv.conf
search Belkin
nameserver 192.168.2.1
- ifconfigg:
addi@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:4E:A1:C1
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5125 errors:1 dropped:0 overruns:0 frame:0
          TX packets:4950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5388669 (5.1 MiB)  TX bytes:563447 (550.2 KiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3640651 (3.4 MiB)  TX bytes:3640651 (3.4 MiB)

I am comfortable moving around and editing on the command line but I know nothing about networks, etc.  Any ideas on what to do next?

---

### Post by add1sun on 2006-04-04
bump.  no ideas??

---

### Post by jamesr on 2006-04-04
Have you tried pinging various places ,
1st the router,
2nd then your ISP
3rd then Google

also using traceroute

---

### Post by add1sun on 2006-04-14
Hm, well I dunno what any of it really means so if anyone sees anything interesting. please speak up.

PINGS----------------------------------------
router:
--- 192.168.2.1 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22032ms
rtt min/avg/max/mdev = 1.147/204.279/994.184/206.662 ms

ISP:
--- 68.54.80.5 ping statistics ---
23 packets transmitted, 23 received, 0% packet loss, time 22011ms
rtt min/avg/max/mdev = 13.666/372.368/1244.598/367.659 ms, pipe 2

google:
--- [www.google.com](www.google.com) ping statistics ---
26 packets transmitted, 26 received, 0% packet loss, time 25021ms
rtt min/avg/max/mdev = 30.832/574.593/1272.027/404.162 ms, pipe 2

TRACEROUTE------------------------------
ISP:
traceroute to 68.54.80.5 (68.54.80.5), 30 hops max, 38 byte packets
 1  192.168.2.1 (192.168.2.1)  581.154 ms  2.198 ms  1.688 ms
 2  73.135.122.1 (73.135.122.1)  17.604 ms  10.928 ms  9.958 ms
 3  ge-2-4-ur01.waldorf.md.bad.comcast.net (68.87.132.125)  20.355 ms  9.894 ms  6.989 ms
 4  * te-9-1-ur01.ellicttcty.md.bad.comcast.net (68.87.128.250)  465.041 ms  554 .968 ms
 5  te-8-1-ur01.catonsville.md.bad.comcast.net (68.87.128.193)  20.269 ms  8.947  ms  19.210 ms
 6  te-9-1-ur01.essex.md.bad.comcast.net (68.87.128.206)  21.737 ms  10.972 ms *
 7  te-8-2-ur01.whitemarsh.md.bad.comcast.net (68.87.129.6)  404.952 ms  10.960 ms  20.969 ms
 8  te-8-2-ur02.whitemarsh.md.bad.comcast.net (68.87.129.170)  19.004 ms  10.921  ms  18.749 ms
 9  te-9-3-ar01.whitemarsh.md.bad.comcast.net (68.87.129.165)  18.944 ms  9.924 ms  20.771 ms
10  68.87.16.145 (68.87.16.145)  19.018 ms  9.857 ms  9.904 ms
11  68.87.16.22 (68.87.16.22)  21.115 ms  12.937 ms  12.951 ms
12  68.87.18.34 (68.87.18.34)  18.993 ms  13.949 ms  28.967 ms
13  68.54.80.53 (68.54.80.53)  20.980 ms *  383.271 ms
14  * 68.54.80.53 (68.54.80.53)  1131.064 ms !A *
15  * * 68.54.80.53 (68.54.80.53)  1305.537 ms !A
16  68.54.80.53 (68.54.80.53)  19.310 ms !A * *
17  * 68.54.80.53 (68.54.80.53)  20.305 ms !A  13.851 ms !A

google:
traceroute: Warning: [www.google.com](www.google.com) has multiple addresses; using 64.233.179.104
traceroute to [www.l.google.com](www.l.google.com) (64.233.179.104), 30 hops max, 38 byte packets
 1  192.168.2.1 (192.168.2.1)  4.485 ms  2.266 ms  1.604 ms
 2  73.135.122.1 (73.135.122.1)  17.468 ms  483.953 ms  9.950 ms
 3  ge-2-4-ur01.waldorf.md.bad.comcast.net (68.87.132.125)  16.730 ms  9.912 ms  9.955 ms
 4  * te-9-1-ur01.ellicttcty.md.bad.comcast.net (68.87.128.250)  553.943 ms  8.9 67 ms
 5  te-8-1-ur01.catonsville.md.bad.comcast.net (68.87.128.193)  19.854 ms  9.927  ms  19.217 ms
 6  te-9-1-ur01.essex.md.bad.comcast.net (68.87.128.206)  311.909 ms  10.927 ms  9.955 ms
 7  te-8-2-ur01.whitemarsh.md.bad.comcast.net (68.87.129.6)  18.888 ms  10.746 m s *
 8  te-8-2-ur02.whitemarsh.md.bad.comcast.net (68.87.129.170)  566.017 ms  10.91 7 ms  21.910 ms
 9  te-9-3-ar01.whitemarsh.md.bad.comcast.net (68.87.129.165)  19.227 ms  458.01 4 ms  17.867 ms
10  68.87.16.137 (68.87.16.137)  21.428 ms  9.945 ms  11.299 ms
11  12.118.149.21 (12.118.149.21)  19.011 ms *  497.840 ms
12  tbr2-p014001.n54ny.ip.att.net (12.123.3.14)  20.550 ms  487.998 ms  16.919 m s
13  ggr2-p390.n54ny.ip.att.net (12.123.3.62)  19.969 ms  15.961 ms  15.966 ms
14  so-8-0-0.car3.NewYork1.Level3.net (4.68.127.149)  22.979 ms *  477.762 ms
15  ae-1-51.bbr1.NewYork1.Level3.net (4.68.97.1)  19.134 ms  488.954 ms ae-1-53. bbr1.NewYork1.Level3.net (4.68.97.65)  15.966 ms
16  as-3-0.bbr1.Washington1.Level3.net (64.159.3.254)  20.943 ms as-3-0.bbr2.Was hington1.Level3.net (4.68.128.206)  18.975 ms as-3-0.bbr1.washington1.level3.net  (64.159.3.254)  19.979 ms
17  ae-22-52.car2.Washington1.Level3.net (4.68.121.51)  1304.222 ms ae-22-56.car 2.Washington1.Level3.net (4.68.121.179)  17.847 ms ae-12-51.car2.Washington1.Lev el3.net (4.68.121.19)  23.938 ms
18  unknown.Level3.net (166.90.148.174)  34.950 ms 4.79.228.26 (4.79.228.26)  32 .974 ms 4.79.18.198 (4.79.18.198)  1364.994 ms
19  72.14.238.232 (72.14.238.232)  536.821 ms 66.249.95.123 (66.249.95.123)  140 3.961 ms 72.14.238.232 (72.14.238.232)  456.594 ms
20  72.14.238.97 (72.14.238.97)  30.945 ms 66.249.95.149 (66.249.95.149)  1212.7 70 ms 72.14.238.97 (72.14.238.97)  30.935 ms
21  72.14.239.17 (72.14.239.17)  1379.946 ms 72.14.238.151 (72.14.238.151)  64.9 42 ms 72.14.232.147 (72.14.232.147)  749.868 ms
22  72.14.238.178 (72.14.238.178)  62.948 ms  34.935 ms  33.962 ms
23  64.233.179.104 (64.233.179.104)  67.977 ms  1380.375 ms  37.888 ms

---

### Post by graigsmith on 2006-04-14
what kernel are you running?

---

### Post by add1sun on 2006-04-15
whatever the latest breezy one is...

addi@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

Note that I am running the x86 version on an Athlon 64.

---

### Post by add1sun on 2006-05-10
Well, here's hoping that Dapper fixes this for me.  I love Ubuntu but we are talking about moving to 15 mbs service and I will want to actually be able to use it all.  If Ubuntu can't give me better speed then I'll have to move to another distro.  yech.

---

