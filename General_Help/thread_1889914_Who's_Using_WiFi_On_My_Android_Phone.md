---
title: "Who's Using WiFi On My Android Phone"
date: 2011-12-02
forum: General Help
---

### Post by codethulhu on 2011-12-02
First of all, I'm still pretty new to Linux and a lot of networking terms.

I'm using my android smart phone as a wifi hotspot with no security enabled (only for a short time). I was wondering how I could tell who all and how many people are connected to my smart phone pseudo-route?. I know I could simply look at my phone but I was wondering if I could gather such information using some tool such as nmap?

Thanks :)

---

### Post by |{urse on 2011-12-02
I believe you can install the aircrack-ng suite on android (I've never done it on android). Seeing as how you will be using it for defense rather than offense..

Install aircrack-ng (good luck)
Get to a command prompt.

airmon-ng start wlan0
airodump-ng mon0

That's it, poke thru the results for ips.
Use nmap to learn more once you think you know who it is..

---

### Post by Lars Noodén on 2011-12-02
nmap would not tell you anything in this context, it can only tell you the open ports not the connections.  netstat or wireshark will be able to show the connections.

---

### Post by |{urse on 2011-12-02
Once u have an ip from airodump and plug it in nmap does it not resolve to a hostname? Thus giving a clue as to location and service provider?

---

### Post by matt_symes on 2011-12-02
Hi

```
sudo nmap -sP XXX.XXX.XXX.XXX/class
```will try a variety of pinging techniques to see who is on your subnet. 

To give an example.....

sudo nmap -sP 192.168.1.0/24

```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$ sudo nmap -sP 192.168.1.0/24
[sudo] password for matthew: 
Starting Nmap 5.21 ( http://nmap.org ) at 2011-12-02 22:03 GMT
Nmap scan report for DD-WRT (192.168.1.1)
Host is up (0.00022s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Unknown)
Nmap scan report for Mark-PC (192.168.1.101)
Host is up (0.0016s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Unknown)
Nmap scan report for my-PC (192.168.1.102)
Host is up (0.00016s latency).
MAC Address: xx:xx:xx:xx:xx:xx (Unknown)
Nmap scan report for matthew-Aspire-7540 (192.168.1.105)
Host is up.
Nmap done: 256 IP addresses (4 hosts up) scanned in 2.97 seconds
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$
```Kind regards

---

