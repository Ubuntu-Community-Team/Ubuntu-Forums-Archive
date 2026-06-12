---
title: "Lots of hits on ports after Firestarter install...?"
date: 2006-03-18
forum: General Help
---

### Post by Joey French on 2006-03-18
How concerned should I be about hits recorded by Firestarter? I have apache running on port 80, and another server running on 8080. I have seen hits to these ports in the little while since install of the firewall:
```
Time:Mar 18 08:38:03 Direction: Unknown In:eth0 Out: Port:80 Source:24.107.53.128 Destination:24.168.196.127 Length:48 TOS:0x00 Protocol:TCP Service:HTTP
Time:Mar 18 08:38:56 Direction: Unknown In:eth0 Out: Port:1027 Source:204.16.208.117 Destination:24.168.196.127 Length:500 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:38:56 Direction: Unknown In:eth0 Out: Port:1026 Source:204.16.208.117 Destination:24.168.196.127 Length:500 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:43:07 Direction: Unknown In:eth0 Out: Port:1026 Source:204.16.208.116 Destination:24.168.196.127 Length:498 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:43:07 Direction: Unknown In:eth0 Out: Port:1027 Source:204.16.208.116 Destination:24.168.196.127 Length:498 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:47:39 Direction: Unknown In:eth0 Out: Port:1026 Source:204.16.208.60 Destination:24.168.196.127 Length:491 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:47:45 Direction: Unknown In:eth0 Out: Port:1026 Source:65.149.8.45 Destination:24.168.196.127 Length:1245 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:51:56 Direction: Unknown In:eth0 Out: Port:1026 Source:204.245.216.158 Destination:24.168.196.127 Length:908 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:52:26 Direction: Unknown In:eth0 Out: Port:1026 Source:88.253.69.96 Destination:24.168.196.127 Length:516 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:52:29 Direction: Unknown In:eth0 Out: Port:1026 Source:216.124.208.236 Destination:24.168.196.127 Length:908 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:54:00 Direction: Unknown In:eth0 Out: Port:1027 Source:204.16.208.112 Destination:24.168.196.127 Length:446 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:54:00 Direction: Unknown In:eth0 Out: Port:1026 Source:204.16.208.112 Destination:24.168.196.127 Length:446 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 08:59:24 Direction: Unknown In:eth0 Out: Port:1026 Source:65.212.163.37 Destination:24.168.196.127 Length:1245 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 09:08:00 Direction: Unknown In:eth0 Out: Port:1026 Source:12.38.245.152 Destination:24.168.196.127 Length:250 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 09:15:15 Direction: Unknown In:eth0 Out: Port:1026 Source:65.123.206.101 Destination:24.168.196.127 Length:985 TOS:0x00 Protocol:UDP Service:Unknown

```

Should I be alarmed? I have set rules for incoming on only 80 and 8080, any other opinions? Also, I have gone to the "Lookup Hostnames" option, but the process just dies. 

Thanks for the help.

---

### Post by trotski on 2006-03-18
Heh, you're going to see a LOT of scans.  They happen all the time.  Most are (still) windows messenger spam pop-ups.  Others are worms, bots sniffing for backdoors.  All of them are Windows-specific, though.  Ports 80 and 8080 are pretty much the most common ports for web servers.  They will always be scanned for possible exploits.  Some folks who only want to use their web server for personal use will simply put it on a very unusual port number.

---

### Post by Carmack78 on 2006-03-18
195.174.X.X is my ISP's network and I'm all kind of scan from those infected machines. Microsoft-ds (directory services), Ms-sql-s (sql server), Samba is scanned all the time. 

```
Time:Mar 18 16:11:31 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.142.182 Destination:195.174.102.156 Length:64 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:12:39 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.231.235 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:12:56 Direction: Unknown In:eth0 Out: Port:137 Source:83.117.247.134 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Mar 18 16:12:57 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.65.91 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:15:32 Direction: Unknown In:eth0 Out: Port:137 Source:206.227.20.103 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Mar 18 16:15:58 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.64.235 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:18:04 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.17.9 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:18:05 Direction: Unknown In:eth0 Out: Port:137 Source:85.108.96.123 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Mar 18 16:18:20 Direction: Unknown In:eth0 Out: Port:137 Source:201.45.46.194 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Mar 18 16:18:25 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.65.91 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:19:13 Direction: Unknown In:eth0 Out: Port:445 Source:220.163.46.9 Destination:195.174.102.156 Length:343 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 16:20:01 Direction: Unknown In:eth0 Out: Port:1025 Source:84.234.223.32 Destination:195.174.102.156 Length:343 TOS:0x00 Protocol:UDP Service:Unknown
Time:Mar 18 16:24:11 Direction: Unknown In:eth0 Out: Port:137 Source:61.221.114.230 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Mar 18 16:25:18 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.30.103 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:26:43 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.115.38 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:33:32 Direction: Unknown In:eth0 Out: Port:1433 Source:193.173.121.52 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Ms-sql-s
Time:Mar 18 16:34:23 Direction: Unknown In:eth0 Out: Port:445 Source:195.174.0.149 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:Microsoft-ds
Time:Mar 18 16:35:57 Direction: Unknown In:eth0 Out: Port:135 Source:195.174.5.201 Destination:195.174.102.156 Length:48 TOS:0x00 Protocol:TCP Service:DCOM-scm
Time:Mar 18 16:37:06 Direction: Unknown In:eth0 Out: Port:137 Source:85.107.95.229 Destination:195.174.102.156 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
```


It's just normal. Internet is a wild, chaotic places with all kind of zombie machines, viruses, etc...

The MOST IMPORTANT thing is your ports (except 80, 8080 services ports) must be STEALTHED. Which means, when someone asks for a FTP server (port:21), your server SHOULD NOT reply with 'not available' answer, INSTEAD it MUST just sit there, giving no answer, so that the attacker/scanner would think there is no computer at the given IP address. It makes port-scan attacks much harder, because until time-out scanner HAS TO WAIT for an answwer.

Just, head to [www.grc.com](www.grc.com) and scan your ports. It will list open/close/shtealted ports. 

If you are using your computer as a personel server like me, just close this ports on firewall.It will NOT effect your [http://localhost](http://localhost) workings. Your services will be available to you.

Hope, this clarify things.

---

### Post by Joey French on 2006-03-18
So, Maybe I should be using stealthing in Firestarter, blacklisting everything but 80 and 8080, or what? To tell you the truth I have only started using it today, so I set it up how I "think" it's supposed to be (setting up rules?). 

Any good advice on setup is appreciated.

Joey

---

### Post by hamsteri on 2006-03-18
You will see lots of hist, mostly portscans.
Just drop (stealth) the packages as mentioned earlier.

---

