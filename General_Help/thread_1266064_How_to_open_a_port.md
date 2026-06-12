---
title: "How to open a port?"
date: 2009-09-14
forum: General Help
---

### Post by djbushido on 2009-09-14
I am trying to open a port on my computer. Checking the port from the windows machine shows that it is open, yet linux marks it closed. Is there anything I can do to fix this?

EDIT:It should be noted that ufw is not on, the router I am on does NOT block the port (proven from windows). If I missed any other details, let me know.

---

### Post by t0p on 2009-09-14
If you're not using a firewall (ie you haven't configured iptables and haven't installed another firewall app), then all ports in ubuntu are "closed" because there are no services running on them.  If you want to "open" port 22 to run an ssh server on it, you simply install and run an ssh server (ie install openssh-server) and have it run when the computer boots.  When you boot, sshd will start, and port 22 will be "open".

---

### Post by stephen.robin on 2009-09-14
Hi

[LEFT][FONT=Verdana][SIZE=2]For the open ports on a computer,      you can use netstat command line.[/SIZE][/FONT][FONT=Arial Black][SIZE=2]To display all open ports, open DOS command, type *       netstat* and press Enter. [/SIZE][/FONT][FONT=Arial Black][SIZE=2]To list all listening ports, use *       netstat -an |find /i "listening"* command.[/SIZE][/FONT][FONT=Arial Black][SIZE=2]To see what ports your computer        actually communicates with, use [/SIZE][/FONT][FONT=Arial Black][SIZE=2]*netstat -an |find        /i "established". *[/SIZE][/FONT][FONT=Arial Black][SIZE=2]To find specified open port, use find switch. For        example, to find if the port 3389 is open or not, do *       netstat -an |find /i "3389". *[/SIZE][/FONT][FONT=Arial Black][SIZE=2]You can use PULIST from the Windows        Resource Kit to find which process is using a specified port. [/SIZE][/FONT][/LEFT]
     [IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]:guitar:

---

### Post by sunchiqua on 2009-09-14
Show us the output of the following command.

```
sudo iptables -L
```

---

### Post by djbushido on 2009-09-14
sudo iptables: ```
brad@BRAD:~$ sudo iptables -L
[sudo] password for brad:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Let me clarify what I am trying to do. I am trying to permanently open a port on my computer to allow for Bittorrent traffic. Currently, my router accepts unrequested connections, not the computer (this obtained by doing the same test with windows). I have not installed any firewall software, or anything else that would close ports other than ubuntu itself. How now do I go about permanently opening a port to use for bittorrent, etc.?

---

### Post by The Cog on 2009-09-14
The iptables listing shows you are not blocking any ports with firewall software. So nothng is stopping incoming connections (provided something is listening for them).

All you need to do is run the bit torrent program. No bit-torrent program running, the port is closed. Program running, it opens the port.

Were you running bit-torrent when you did the port scan?

---

### Post by sunchiqua on 2009-09-14
Turn on your torrent client ( wait a few minutes before continuing ) and let us know, do you see your port in the output of the following command ?

```
netstat -al | grep LISTEN

```

---

### Post by djbushido on 2009-09-14
The port is in netstat, but online tools show it still being closed.

---

### Post by scrooge_74 on 2009-09-14
I hate ufw to manage iptables, I prefer using firehol or if you are not to fond of CLI you can use firestarter so you can config using the GUI

---

### Post by stderr on 2009-09-14
> **The Cog said:**
> All you need to do is run the bit torrent program. No bit-torrent program running, the port is closed. Program running, it opens the port.

Were you running bit-torrent when you did the port scan?

My thoughts exactly. Which bittorrent client daemon, or application, are you running? Double check which port it's configured to use, etc. You should not need to worry about the firewall since it isn't set to do anything. There's nothing to "open" - you just need to run the client...

***If*** you had configured iptables, or were running something like GUFW, Firestarter etc, ***then*** you'd need to worry about opening ports.

---

### Post by Slim Odds on 2009-09-14
> **djbushido said:**
> ]Let me clarify what I am trying to do. I am trying to permanently open a port on my computer to allow for Bittorrent traffic. Currently, my router accepts unrequested connections, not the computer (this obtained by doing the same test with windows). I have not installed any firewall software, or anything else that would close ports other than ubuntu itself. How now do I go about permanently opening a port to use for bittorrent, etc.?

You need to configure your router to forward those ports to your computer. Check the router documentation.

On my linksys unit, it's under the "Applications & Gaming" section.

---

### Post by denver on 2009-09-14
> **djbushido said:**
> sudo iptables: ```
brad@BRAD:~$ sudo iptables -L
[sudo] password for brad:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
Let me clarify what I am trying to do. I am trying to permanently open a port on my computer to allow for Bittorrent traffic. Currently, my router accepts unrequested connections, not the computer (this obtained by doing the same test with windows). I have not installed any firewall software, or anything else that would close ports other than ubuntu itself. How now do I go about permanently opening a port to use for bittorrent, etc.?

Sounds like you want port forwarding. If i understand correctly, you want to allow clients to connect to you without you connecting to them initially. The easiest way this can be accomplished is with the help of uPnP (universal Plug and Play). Most home routers have this feature installed and it basically does all the dirty work for you. Also, most torrent clients also use this feature by default.

If however, you prefer the more difficult manual way, then you have to do 3 things. First, allocate a static IP address for your laptop while connected to the router at home. This can be done by going to nm-applet-->edit connections-->wired/wireless. Select your connection and hit edit. Under IPv4 settings you should be able to set IP, Gateway, Netmask and DNS servers.

After that you need to login to your router's web interface and choose a port (above 1024) that you should forward to the IP address you just set for your laptop.

And last, fire up your favorite torrent client, and set the default port to listen on to be the same one you forwarded on your router. You should now be able to receive incoming connections from your peers. 

Good luck!

---

### Post by djbushido on 2009-09-16
Yeah, that's what I found out the windows computer was doing.
Here is the Truth:
1. Ubuntu uses dynamic ports - when an application wants a port open, it becomes open - the port can accept unrequested connections - however:
2. The router by default does not know to forward packets aimed at a certain port to that IP address - so while ubuntu will accept the unrequested connections, the router does not know to give the connections to ubuntu.
3. This is where portforwarding/static IP or UPnP comes in - if you forward a port to a static IP, then it is truly open - UPnP does the same thing, only dynamically.

If there are any more questions, let me know.

---

### Post by Slim Odds on 2009-09-16
> **djbushido said:**
> 
2. The router by default does not know to forward packets aimed at a certain port to that IP address - so while ubuntu will accept the unrequested connections, the router does not know to give the connections to ubuntu.


That's exactly what I was saying......

Just another note: the "unrequested connection" does not make sense. The remote host is requesting the connection.

---

### Post by djbushido on 2009-09-16
But with bittorrent, there may be unrequested connections: I.e. if someone else has an upload slot open, the torrent client will try and upload to somebody. If the second client did not ask/request that connection, it will be blocked by the router, because the router does not know what to do with it.

---

### Post by Slim Odds on 2009-09-17
> **djbushido said:**
> But with bittorrent, there may be unrequested connections: I.e. if someone else has an upload slot open, the torrent client will try and upload to somebody. If the second client did not ask/request that connection, it will be blocked by the router, because the router does not know what to do with it.

OK, now I understand what you where trying to say. Just to mention again that the term "unrequested connection" just does not make sense in any context.

The answer to this issue is that you need to forward a range of addresses to the local host. Not just one.

---

### Post by denver on 2009-09-18
> **djbushido said:**
> Yeah, that's what I found out the windows computer was doing.
Here is the Truth:
1. Ubuntu uses dynamic ports - when an application wants a port open, it becomes open - the port can accept unrequested connections - however:
2. The router by default does not know to forward packets aimed at a certain port to that IP address - so while ubuntu will accept the unrequested connections, the router does not know to give the connections to ubuntu.
3. This is where portforwarding/static IP or UPnP comes in - if you forward a port to a static IP, then it is truly open - UPnP does the same thing, only dynamically.

If there are any more questions, let me know.

"Dynamic ports" also makes no sense. Ubuntu itself does not open any ports. The application opens up ports whenever it needs to.

In any TCP/IP connection there are always 2 types of ports involved:

- source port
- destination port

The source port is indeed random and is used to receive a response from the destination. When connecting to others the source port is opened on your PC and is used to comunicate with the destination PC (destination port - the port the BitTorrent client listens on). 

Most home "routers" actually perform some form of NAT (Network Address Translation) or another. In any NAT environment there is a "feature" or a system called "Connection tracking". This system is responsible for mapping every connection initiated by the PC's behind it, so that when a response from the destination (other people YOU connect to) arrives back, it is sent to the correct PC. You do NOT have to do this by yourself. It is done automatically by your router.

Now, what's REALLY important here is the "DESTINATION PORT". The "destination port" (port the torrent client listens on) on any torrent client is always the same, and this is used to receive incoming connections from other clients. This is the only port you need to forward manually (and the only one you need to worry about). This port is advertised by your bittorrent application to all other clients in the swarm so they know where to connect. As long as you have one port open and this port is set as the "Port for incoming connections" (see Transmission BitTorrent Client) you should be able to receive incoming connections from other clients. 

As a side note, although its not fair to others, you are not required to open a port in order to download a torrent. Not opening up a port will prevent others from downloading from you while you are seeding, but you should be able to perform downloads without problems. Some slowdowns may be experienced though.

Hope this clears up some of the ambiguity and inner workings of incoming and outgoing connections. :)

Best of luck!

---

### Post by djbushido on 2009-09-19
> **denver said:**
> "Dynamic ports" also makes no sense. Ubuntu itself does not open any ports. The application opens up ports whenever it needs to.
True, but by the same token, Windows ports are "open" by default - all are activated through UPnP, while Ubuntu "closes" all by default unless an application requests that they become open. Thats what I really meant, sorry.

---

### Post by denver on 2009-09-19
If you use Transmission BitTorrent client, go to:

Edit-->Preferences-->Network

And check the box that says:

Use UPnP or NAT-PMP fort forwarding from my router

and you should have the same result you do in Windows. 

The operating system itself rarely (if ever?) uses UPnP. Thats usually the application's job. Also, neither windows nor any other operating system i know opens up ALL ports. For a port to be open, an application must first request a port from the operating system, then bind to it and then listen on it.

But as i said before, there are 2 types of ports. Only one of them actually listens for incomming connections. The other one is used only to establish an outgoing connection (these are always "open"). 

There are 65536 usable ports (if i am not mistaken) out of which 1024 are privilaged ports (common services like www, email, DNS).

In any case, if you do deside to use UPnP, and your router suports it, then no manual port forward is needed. You should be good to go as long as you tell your torrent client to use UPnP as well.

---

### Post by djbushido on 2009-09-19
What happens on windows is that not all ports are listening - but they will accept connections aimed at them: no port forwarding is needed. While that doesn't make total sense, basically windows needs no port forwarding. Linux by default DOES NOT use UPnP because of the huge security vulnerabilities. The first 1024 ports are also blocked totally to applications unless they are standards - like 80 for http, 22 for ssh, etc. So if you try to configure an email client to use a port below 1024, it will be blocked. Or at least, that's what happened to me with Thunderbird.

Also, I use KTorrent, and I'm not sure how to use UPnP with that. Or whether I actually will.

---

### Post by denver on 2009-09-20
You are confusing clients with servers.....

Both use ports to communicate, like i said, there are 2 types. One type accepts incoming connections (servers), one does not (clients).

Here is a little info on the TCP stack:

```
http://en.wikipedia.org/wiki/Transmission_Control_Protocol
```

Windows follows the same TCP/IP rules as any other OS. If an application is not listening on a particular port (server), then that port is NOT open.

There is also a difference between closed ports and blocked ports. Closed ports are ports that are not used by any application to accept incoming connections on.

Blocked ports are ports already opened by an application (server), but access to them is restricted by some mechanism (be it a firewall or something else). By default Ubuntu has no firewall rules that block your ports.

Torrent clients are both clients and servers, that's why you need to listen on a certain port for incoming connections.

UPnP is an auto negotiation protocol that communicates with your router and basically "tells" it to forward a port to the PC using UPnP. There is no risk in using UPnP at all. Having a port forwarded to you automatically is only dangerous if you grant remote access to your system through that port (SSH, RSH or whatever) and the service that actually listens on that port is itself vulnerable. 

The first 1024 are called privileged ports because, in linux at least, you need root access to open or bind to (if i am not mistaken).

An e-mail client DOES NOT, i repeat, DOES NOT listen on any port for incoming connections. An e-mail client only initiates outgoing connections. You do not need port forwarding or UPnP for that.

If you cannot connect to an e-mail server using Thunderbird and port 25, that its more likely that your ISP or email provider does not allow outgoing (ISP) or incoming (email provider) connections to or from they're network. Contact your ISP for more info.

Most email providers offer alternate ports for SMTP: 587 and 465 which you can try out. You will get the same result in windows and linux alike.

Please go to:

```
http://en.wikipedia.org/wiki/TCP_ports
```

for a little lite reading on what ports actually are and how they work. I also recommend reading the first module of the Cisco Certified Network Associate curriculum to get a better grasp on how a network connection is established and how information travels across different layers of a network.

An open port does not automatically give you unrestricted access to a system. It only allows you to connect to a service that uses that port to accept connections (email, DNS, www).

To make an analogy, think of a port as a door on a house. Now think of firefox as a traveling salesman that had to walk out his door (source port) in order to get to that house. If the destination port (door) is closed, the salesman (firefox) will go home hungry and sad. If the door (port) is open, the salesman will negotiate with the occupant of the house (server) so they can start exchanging information (requests for webpages, and the actual webpages). The salesman goes back home happy and with a little something to feed he's family.

KTorrent has implemented UPnP in the form of a plugin. Go to:

Settings-->Configure KTorrent-->Plugins

And search for UPnP. You should be able to select it. After you hit apply, you should have an icon in the lower part of your main window that reads "UPnP".

---

### Post by djbushido on 2009-09-20
...Just when I thought I had everything figured out...
Thanks for the Ktorrent info!
However, this still does not explain why web services found a port open on windows and not on linux. To be specific, 39600.

---

### Post by denver on 2009-09-20
Like i sayd a few times :), if an application requests a port from the operating system, it will be opened. Maybe you have a service running on that particular port in windows that si not running in Ubuntu.

One nifty way to find out, both in Ubuntu and in windows is the:

```
netstat
```

command. Running netstat in Ubuntu with the following parameters:

```
netstat -tuapn
```

will show you all UDP and TCP connections, the program name that uses those connections and it will not rezolve IP's into domain names (PTR records - faster output this way). I am not familiar with the command line options in windows but you should be able to see a help message if you type in:

```
netstat /?
```

if i remember correctly (sorry if my memory fails me, its been 5 years since i have used windows).

In both cases you should be looking for services that have the status "LISTEN". Here are a few examples on my system:

```

$ sudo netstat -tuapn
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:1194          0.0.0.0:*               LISTEN      5268/openvpn    
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      3501/smbd       
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      3439/portmap    
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      3468/dnsmasq       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3899/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      3501/smbd 

```

The status "LISTEN" means that there are services waiting for incomming connections on the ports mentioned after the ":".

Hope this clears up some of your questions.

Good luck!

---

