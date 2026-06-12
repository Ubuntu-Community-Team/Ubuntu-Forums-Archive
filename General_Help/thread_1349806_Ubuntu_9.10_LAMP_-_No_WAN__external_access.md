---
title: "Ubuntu 9.10 LAMP - No WAN / external access"
date: 2009-12-08
forum: General Help
---

### Post by beerinder on 2009-12-08
Hi, just installed an Ubuntu 9.10 Server with LAMP, OpenSSH & Webmin. The server is accessible via the LAN (http/https/ssh/ftp). When trying to hit the server via the WAN IP, the site doesn't load; including apache, proftpd, openssh, etc. The server is on a VM, and all the router firewall rules/nat policies are in place and tested by putting up another VM on the same IP and testing via IIS to see if the outside world could access it.
 
According to Webmin, the firewall is set to "Allow all" by default. I'm not sure where to go from here so any help would be appreciated. I'll be hosting multiple websites/domains on the server, all which will be pointing to my single WAN IP which will be routed through the cisco asa to my internal LAMP server ip.
 
See below for some random info which I thought may help. I can ping internal (LAN) ips, and traceroute them. For external domains/ips, if I try a traceroute or ping, it resolves the DNS but has 100% packet loss.
 
Thanks for any help in advance!
 
 
Netstat results:
 
brodey@lslamp01:~$ netstat -ntl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 0 0.0.0.0:443 0.0.0.0:* LISTEN
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:10000 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:21 0.0.0.0:* LISTEN
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN
tcp6 0 0 :::22 :::* LISTEN
 
Host file entries:
 
[COLOR=#008888]127.0[/COLOR][COLOR=#888800].[/COLOR][COLOR=#008888]0.1[/COLOR] localhost[COLOR=#888800].[/COLOR]xxxx[COLOR=#888800].[/COLOR]com localhost 
[COLOR=#008888]192.168[/COLOR][COLOR=#888800].[/COLOR][COLOR=#008888]200.20[/COLOR] lamp01[COLOR=#888800].[/COLOR]xxxx[COLOR=#888800].[/COLOR]com lslamp01 
[COLOR=#008888]208.64[/COLOR][COLOR=#888800].[/COLOR]xxx[COLOR=#888800].[/COLOR]xxx lamp01[COLOR=#888800].[/COLOR]xxxx[COLOR=#888800].[/COLOR]com lslamp01
[COLOR=#aa0000]# The following lines are desirable for IPv6 capable hosts[/COLOR] 
[COLOR=#888800]::[/COLOR][COLOR=#008888]1[/COLOR] localhost ip6[COLOR=#888800]-[/COLOR]localhost ip6[COLOR=#888800]-[/COLOR]loopback 
fe00[COLOR=#888800]::[/COLOR][COLOR=#008888]0[/COLOR] ip6[COLOR=#888800]-[/COLOR]localnet 
ff00[COLOR=#888800]::[/COLOR][COLOR=#008888]0[/COLOR] ip6[COLOR=#888800]-[/COLOR]mcastprefix 
ff02[COLOR=#888800]::[/COLOR][COLOR=#008888]1[/COLOR] ip6[COLOR=#888800]-[/COLOR]allnodes 
ff02[COLOR=#888800]::[/COLOR][COLOR=#008888]2[/COLOR] ip6[COLOR=#888800]-[/COLOR]allrouters 
ff02[COLOR=#888800]::[/COLOR][COLOR=#008888]3[/COLOR] ip6[COLOR=#888800]-[/COLOR]allhosts
 
Traceroute attempt to google:
 
brodey@lslamp01[COLOR=#888800]:~[/COLOR]$ traceroute google[COLOR=#888800].[/COLOR]com 
traceroute to google[COLOR=#888800].[/COLOR]com [COLOR=#888800]([/COLOR][COLOR=#008888]74.125[/COLOR][COLOR=#888800].[/COLOR][COLOR=#008888]67.100[/COLOR][COLOR=#888800]),[/COLOR] [COLOR=#008888]30[/COLOR] hops max[COLOR=#888800],[/COLOR] [COLOR=#008888]60[/COLOR] [COLOR=#0000aa]byte[/COLOR] packets 
[COLOR=#008888]1[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] 
[COLOR=#008888]2[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] 
[COLOR=#008888]3[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] 
[COLOR=#008888]4[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] 
[COLOR=#008888]5[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR] [COLOR=#888800]*[/COLOR]

---

