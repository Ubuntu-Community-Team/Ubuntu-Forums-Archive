---
title: "Can't Access Apache From the Internet"
date: 2011-02-15
forum: General Help
---

### Post by Killing Vector on 2011-02-15
I can access dirac.org from inside my network; I can't access it from outside my home network.  Apache is running on a Ubuntu
box named "satan": 192.168.0.2 and I'm testing it from a MS Windows machine named "lucifer": 192.168.0.3.  My ISP is optimum online, which does not filter port 80.

**0. router**
The router is a Netgear WNDR3700.  All computers on my LAN receive their IP addresses via DHCP, but I've reserved all the IP addresses, so they are essentially static (satan is always 192.168.0.2, lucifer is always 192.168.0.3, etc).  The router is set up to pass packets destined for port 80 to satan (192.168.0.2), which is where Apache runs.

**1. tcpdump**
Using tcpdump when accessing dirac.org from within the LAN (this is what works):

[COLOR="Blue"]# tcpdump -i eth0 host ool-18bda2d2.dyn.optonline.net and tcp port 80
ool-18bda2d2.dyn.optonline.net.2826 > satan.www: Flags [S], seq 3934453911, win 65535, options [mss 1460,nop,nop,sackOK], length 0
satan.www > ool-18bda2d2.dyn.optonline.net.2826: Flags [S.], seq 2824373109, ack 3934453912, win 5840, options [mss 1460,nop,nop,sackOK], length 0
ool-18bda2d2.dyn.optonline.net.2826 > satan.www: Flags [.], ack 1, win 65535, length 0
ool-18bda2d2.dyn.optonline.net.2826 > satan.www: Flags [P.], seq
1:487, ack 1, win 65535, length 486
satan.www > ool-18bda2d2.dyn.optonline.net.2826: Flags [.], ack 487, win 6432, length 0
satan.www > ool-18bda2d2.dyn.optonline.net.2826: Flags [P.], seq
1:211, ack 487, win 6432, length 210
ool-18bda2d2.dyn.optonline.net.2826 > satan.www: Flags [.], ack 211,
win 65325, length 0[/COLOR]


Using tcpdump when accessing dirac.org from outside the LAN
(this doesn't work)

[COLOR="Blue"]# tcpdump -i eth0 host born.physics.ucdavis.edu and tcp dst port 80
born.physics.ucdavis.edu.45830 > satan.www: Flags [S], seq 692754447, win 5840, options [mss 1460, sackOK, TS val 303380783 ecr 0,nop,wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq 3535693591, ack 692754448, win 5792, options [mss 1460,sackOK,TS val 32070833 ecr 303380783, nop, wscale 6], length 0
born.physics.ucdavis.edu.45830 > satan.www: Flags [S], seq 692754447, win 5840, options [mss 1460, sackOK, TS val 303383783 ecr 0,nop,wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq
3535693591, ack 692754448, win 5792, options [mss 1460,sackOK,TS val 32071581 ecr 303380783, nop, wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq
3535693591, ack 692754448, win 5792, options [mss 1460,sackOK,TS val 32071915 ecr 303380783, nop, wscale 6], length 0
born.physics.ucdavis.edu.45830 > satan.www: Flags [S], seq 692754447, win 5840, options [mss 1460, sackOK, TS val 303389783 ecr 0,nop,wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq
3535693591, ack 692754448, win 5792, options [mss 1460, sackOK, TS val 32073081 ecr 303380783,nop,wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq
3535693591, ack 692754448, win 5792, options [mss 1460,sackOK,TS val 32073415 ecr 303380783,nop,wscale 6], length 0
satan.www > born.physics.ucdavis.edu.45830: Flags [S.], seq
3535693591, ack 692754448, win 5792, options [mss 1460,sackOK,TS val 32076415 ecr 303380783,nop,wscale 6], length 0
[/COLOR]

So packets are DEFINITELY reaching my server from outside my LAN.  Port forwarding is working, and satan is acknowledging the packets.  I believe that points to Apache server misconfiguration.  It's interesting that born and satan appear to talking to each other, sending each other syns over and over.

As a corollary, my ISP isn't filtering port 80.  I called them and verified that (I'm allowed to run a webserver under my TOS.)


**2. telnet**
From inside the network, I tried telneting to port 80 from lucifer(the MS Windows machine at 192.168.0.3):

[COLOR="Blue"]C:\Documents and Settings\p>telnet dirac.org 80
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Method Not Implemented</title>
</head><body>[/COLOR]

From outside the network:

[COLOR="Blue"]born.ucdavis.edu$ telnet dirac.org 80
Trying 24.189.162.210...
telnet: connect to address 24.189.162.210: Connection timed out
[/COLOR]
Which is no surprise.  It tells me that Apache isn't listening to
connections from outside the network.  I knew that already.


**3. Apache Configuration**
This is the weak link, I think.  apache2ctl reports no configuration problems:

[COLOR="Blue"]root@satan:/etc/apache2# apache2ctl configtest
Syntax OK[/COLOR]

I'm using name based virtual hosting since I may want to serve two domains from the same IP address in the future.  In apache2.conf:

[COLOR="Blue"]ServerName dirac.org
ServerRoot "/etc/apache2"
NameVirtualHost *:80
ErrorLog /var/log/apache2/error.log
LogLevel debug[/COLOR]

In /etc/apache2/sites-enabled/001-dirac.org:

[COLOR="Blue"]<VirtualHost *:80>
   ServerAdmin [email]p@dirac.org[/email]
   ServerName  [www.dirac.org](www.dirac.org)
   ServerAlias [www.dirac.org](www.dirac.org) dirac.org satan

   DirectoryIndex index.html
   DocumentRoot /www/dirac

   LogLevel debug
   ErrorLog  /var/log/apache2/dirac.org.error
   CustomLog /var/log/apache2/dirac.org.access combined
</VirtualHost>[/COLOR]


And in /etc/apache2/sites-enabled/002-iuselinux.org:

[COLOR="Blue"]<VirtualHost *:80>
   ServerAdmin [email]p@dirac.org[/email]
   ServerName  [www.iuselinux.org](www.iuselinux.org)
   ServerAlias [www.iuselinux.org](www.iuselinux.org) iuselinux.org

   DirectoryIndex index.html
   DocumentRoot /www/iuselinux

   LogLevel debug
   ErrorLog  /var/log/apache2/iuselinux.org.error
   CustomLog /var/log/apache2/iuselinux.org.access combined
</VirtualHost>[/COLOR]


I worked my *** off to get rid of the "NameVirtualHost *:80 has no virtual host" error messages.  I'm no expert, but this looks right to
me.


**4. hosts**
It almost feels like Apache doesn't recognize that http requests from born.ucdavis.edu are coming in for dirac.org, so it ignores these requests.  So perhaps the problem is some other file having to do with server identification.  Here is the contents of /etc/hostname:

[COLOR="Blue"]satan[/COLOR]

and /etc/hosts:

[COLOR="Blue"]127.0.0.1    localhost
192.168.0.1  azazel
192.168.0.2  satan
192.168.0.2  dirac.org
192.168.0.2  [www.dirac.org](www.dirac.org)
192.168.0.3  lucifer

192.68.0.50  mara
192.68.0.51  demogorgon
192.68.0.52  belial
192.68.0.53  orcus
192.68.0.54  jublex
192.68.0.55  asmodeus
[/COLOR]

I'm at a complete loss here.  I'd really appreciate some help here.  I really don't know what to do next.  I've collected a bunch of data, but can't figure out where to go from here.

Thanks!
Pete

---

### Post by hawkmage on 2011-02-15
When using named hosts in Apache testing using telnet is not going to quite work the way you expect.  There is a HTTP header for HOST that is used by Apache to determine which virtual is going to respond to your request.  I will usually use something like curl to test since it is HTTP 1.1 complaint and includes the HOST header.  

Since you are seeing TCP traffic to port 80 but getting no response it does lok like there is an issue with Apache finding the VirtualHost it is supposed to use.

---

### Post by Habitual on 2011-02-15
"outside my home network" your apache's IP is NOT 192.168.x.x
it should be the the "hard" IP of the router:80

---

