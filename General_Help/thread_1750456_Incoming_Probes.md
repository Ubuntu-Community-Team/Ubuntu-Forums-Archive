---
title: "Incoming Probes"
date: 2011-05-05
forum: General Help
---

### Post by SparTacux on 2011-05-05
Weird one this.

Quite often when I first power up my modem router ( NETGEAR DG834GT ) my router logs show my modem being bombarded with incoming traffic from a variety of sources but strangely they are aimed at the same port. Today the port being probed  is UDP /TCP port 28776. My modem router sends its logs on port 514 ( SYSLOG )  to my laptop. On the laptop I can view the live traffic from any computer on my network by running System Log Viewer and opening the modem log file I created. Using fixed IP addresses for each computer I can see what traffic comes  from any particular PC.

As I stated, my modem router is 'often' bombarded with traffic aimed at just one port but from many different sources & as yet I am unable to work out the reason for it. I thought I'd chuck it up here to see what you guys come up with.

In the example below you can see my router come on then Immediately I get the probes. These probes to port 28776 went on for an hour or so until I decided to reboot the router and pick up a new IP address. I had the same thing happen yesterday except the port was port 51858.

Any ideas?
 
May  5 17:34:24 Initialize LCP.
May  5 17:34:24 LCP is allowed to come up.
May  5 17:34:24 CHAP authentication success
May  5 17:34:24 UDP Packet - Source:87.202.138.226,21145 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 TCP Packet - Source:92.3.185.48,51430 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 TCP Packet - Source:68.151.45.235,54285 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:89.137.118.9,15921 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 TCP Packet - Source:46.189.164.12,59922 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:79.142.59.234,64781 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:89.136.45.92,62594 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 Send out NTP request to 91.189.94.4
May  5 17:34:24 Receive NTP Reply from 91.189.94.4
May  5 17:34:24 UDP Packet - Source:89.101.179.38,60881 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:86.80.111.240,6480 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:188.107.8.76,50955 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:79.164.46.236,14521 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:87.202.138.226,21145 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:113.17.161.207,2668 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 TCP Packet - Source:68.151.45.235,54285 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,58251 Destination:194.72.6.57,53 - [DNS rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,41848 Destination:194.72.6.57,53 - [DNS rule match]
May  5 17:34:24 UDP Packet - Source:81.233.219.51,13514 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [NTP rule not match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [OUTBLOCKU rule match]
May  5 17:34:24 UDP Packet - Source:89.137.118.9,15921 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:113.17.161.207,2668 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:201.243.182.132,33075 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:89.136.45.92,62594 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:89.101.179.38,60881 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [NTP rule not match]
May  5 17:34:24 UDP Packet - Source:192.168.0.236,123 Destination:91.189.94.4,123 - [OUTBLOCKU rule match]
May  5 17:34:24 UDP Packet - Source:90.151.184.175,49803 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:71.105.182.236,60356 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.231,58704 Destination:194.73.82.242,53 - [DNS rule match]
May  5 17:34:24 UDP Packet - Source:92.113.119.220,48389 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.231,123 Destination:91.189.94.4,123 - [NTP rule match]
May  5 17:34:24 UDP Packet - Source:192.168.0.231,43753 Destination:194.72.6.57,53 - [DNS rule match]
May  5 17:34:24 UDP Packet - Source:87.221.28.17,14510 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 TCP Packet - Source:85.167.42.13,20019 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:139.142.163.26,5321 Destination: x.x.248.106,28776 - [INBLOCK rule match]
May  5 17:34:24 UDP Packet - Source:91.103.79.47,20855 Destination: x.x.248.106,28776 - [INBLOCK rule match]
M

---

