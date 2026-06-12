---
title: "Configuring apt-cacher-ng thru Cisco Router"
date: 2009-12-10
forum: General Help
---

### Post by praveensripati on 2009-12-10
Hi,

I have got a Server (192.168.0.100) an a NetBook (192.168.0.102). Both are connected through a router (Cisco WRT54GH). I am trying to setup apt-cacher-ng and did the following steps (got from [http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085))

1. Installed apt-cacher-ng on the Server.

2. Ran the following on the Server
	echo 'Acquire::http { Proxy "http://localhost:3142"; };' | sudo tee /etc/apt/apt.conf.d/01apt-cacher-ng-proxy

3. Changed the Synaptic Proxy Setting on the Server to
	HTTP Proxy: localhost 3142
	FTP Proxy: localhost 3142

4. Did an apt-get on the Server. Verified that /var/cache is getting populated with the deb files.

5. In the [http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html) on the Server, I got the dashboard.

6. When I run the following on the Server I get 'netstat -an | grep 3142'
tcp        0      0 0.0.0.0:3142            0.0.0.0:*               LISTEN     
tcp6       0      0 :::3142                 :::*                    LISTEN  

7. Ran the following on the NetBook
	echo 'Acquire::http { Proxy "http://192.168.0.100:3142"; };' | sudo tee /etc/apt/apt.conf.d/01apt-cacher-ng-proxy

8. Changed the Synaptic Proxy Setting on the Netbook to
	HTTP Proxy: 192.168.0.100 3142
	FTP Proxy: 192.168.0.100 3142

9. When I do a reload in Synaptic on the Netbook, I get the following message
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 192.168.0.100:3142 (192.168.0.100), connection timed out

10. When I run 'nc -z -v -w2 192.168.0.100 3142' I get
praveensripati-desktop.local [192.168.0.100] 3142 (?) : Connection timed out

When I remove the proxy settings from the Synaptic on the Netbook, it works fine. But, I am getting the timeout errors when I set the Synaptic proxy to the Server. Is it due the Cisco router inbetween the Server and the Netbook? I logged into the Cisco router and tried a couple of things and could not get the Synaptic on the Netbook working.

Can some help me to get this work?

Thanks,
Praveen

---

### Post by praveensripati on 2009-12-11
Hi,

The problem got resolved. I had to make changes to the firewall setting on the Server to open the port and it worked like a charm.

Praveen

---

