---
title: "one way audio, cannot receive calls with VOIP. VOIP configuration with NAT router"
date: 2012-05-10
forum: General Help
---

### Post by Financing Dragons on 2012-05-10
Hello there,

Recently I started a VOIP connection with my ISP. I had to buy ATA box (analog telephone adapter) in order for my analog phone to work over VOIP, upon connecting I was expierencing one way audio and could not receive calls. My isp, xnet, had no clue what it was and after 2 hours of them walking me through unprovailing steps, i decided to do a little research myself. Almost immediatley I found the problem, my NAT router was dropping traffic, because it didn't know where to send it.

The way NAT works is quite simple. When I device on the LAN inciates a connection with a device on the internet, it first sends all traffic to the NAT router. The NAT router then replaces the sources private ip address with a public ip address of its own, before sending the traffic to its destination on the internet. When a response is received, the NAT router searches its translation tables to find the orginal ip address of the device that iniciated the connection then sends it to that device.

When a connection is orginated from a device on the internet, it is not sure what device on the LAN the connection was meant to be established with and the traffic is discraded and the connection is not made.

So in order for VOIP to work with a NAT router, there must be some rule telling it what to do with the incomming traffic, that is destined for the voip device. Some routers support a thing called 'software DMZ' which can handle a simple rule such as, send all incomming connection requests to 192.168.1.5 but unfortunately this did not work for me. So I went to the next solution, Port Fowarding. After forwarding all traffic from the ports that my voip connection was using, to my ATA (if you do not have an ATA box and are using an IP phone, then just forward all traffic to that), my new phoneline was working great, I could receive calls and was no longer expierencing one way audio.

If you are not sure what ports and protocols your voip connction is using, ask your ISP (Internet Service Provider), or alternatively your ATA box or ip phone should list what ports and protocols it is using via the configuration menu.

Your port forwards should look simmilar to this:

voip1

forward external port range
from: 8065
to: 9065
forward traffic to: 192.168.1.5
protocol: tcp/udp
forward internal port range
from: 8065
to: 9065

voip2

forward external port range
from: 3216
to: 3286
forward traffic to: 192.168.1.5
protocol: udp
forward internal port range
from: 3216
to: 3400

voip3

forward external port range
from: 6050
to: 7060
forward traffic to: 192.168.1.5
protocol: tcp
forward internal port range
from: 6050
to: 7060

(I just used random port numbers and protocols here, you will need to contact your ISP to get yours)

Goodluck and enjoy your cheap calling rates,

Tobin
Financing Dragons

---

