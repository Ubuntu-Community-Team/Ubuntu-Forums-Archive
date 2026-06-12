---
title: "Open ports?"
date: 2010-08-03
forum: General Help
---

### Post by Manifest on 2010-08-03
Hi everyone I'm sorta new here so don't get all complicated lol :p
Anyway how do I open ports? I searched google and found nothing,I have no firewall installed on Ubuntu and disabled the firewall on my router but with no avail.
I still only had ports 80 and 22 open.
I opened port 22 by installing ssh in the repositories if thats any help.



Sitting here waiting for an answer:popcorn:

---

### Post by Smart Viking on 2010-08-03
By default all ports are open in ubuntu. There is probably something with your router, enter you IP address in the browser, and you should get promted by username(unless ur IP is forwarded somewhere else) and password, log in with the information that most likely is written under the router(the username is more likely "admin") and look to see of something is blocking it.

Have you done a port scan to see if the ports are closed? :)

---

### Post by jerenept on 2010-08-03
I think ports are only opened when an application or command on the computer opens it. (i.e. ports will only be opened when needed.)

---

### Post by Raymond2201 on 2010-08-03
> **Smart Viking said:**
> By default all ports are open in ubuntu.

Is that a typo? should that not read Windows? hehe

too OP, you can get a GUI for your amazingly complicated Ubuntu firewall , Iptables that ships with Ubuntu.

```
 sudo apt-get install firestarter
```

it should be straight forward to configure after you install it.

---

### Post by Smart Viking on 2010-08-03
> **Raymond2201 said:**
> Is that a typo? should that not read Windows? hehe

Oh is that wrong? :oops:

Sorry about that.. 

[-o< - stupid me-- :P

---

### Post by endotherm on 2010-08-03
well first and formost, reenable the router firewall and use instructions from here on how to forward a port:[http://portforward.com/](http://portforward.com/)
they have instructions for most makes/models
you can test your port here:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)



as for your firewall, the linux firewall has one built in, but it allows all ports by default, so unless you installed a firewall config tool like gufw, or used iptables manually, the firewall is not blocking your port. if you want to install a firewall config tool, use gufw rather than firestarter (its a dead project). you only need to run gufw/firestarter when you want to configure the firewall. don't load them at every boot or login. 

**Keep in mind, a port is only open if an application is listening on it, so just because a port with no app is not open, does not mean it is being blocked.** what app are you trying to contact through your port?

you can test your port internally from another machine by opening a terminal and entering:
```
telnet <sshservername> 22
```if you see a message like this then your port is open:

```

Lucid:~$ telnet win7 139
Trying 10.x.y.z...
Connected to win7.somedomain.com.
Escape character is '^]'.

```if it is closed you will see this instead:
```

telnet: Unable to connect to remote host: Connection timed out

```

or you can install zenmap from the repositories and do a scan on your host to determine what ports are open to what.

---

### Post by Smart Viking on 2010-08-03
Yes, it looks like the OP have runned a port scan and found that only 80 and 22 are one, which are true but they are not blocked, then i guess there is nothing to fix really unless he wanna have them open all the time. :)

Dis i read now(thanks to raymond2201): [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Manifest on 2010-08-04
Firestarter dosn't open ports either even when I turned the routers firewall either
On Firestarter I went to Policy>Right clicked Allow service and added my port
I still get 
```
***-laptop:~$ telnet 127.0.0.1 21
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```
So how do I open ports?

---

### Post by endotherm on 2010-08-04
> **Manifest said:**
> Firestarter dosn't open ports either even when I turned the routers firewall either
On Firestarter I went to Policy>Right clicked Allow service and added my port
I still get 
```
***-laptop:~$ telnet 127.0.0.1 21
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```So how do I open ports?

do you have reason to believe that there is a process listening on port 21? is it ftp? 
what is the output of 
```

netstat -tulp

```
to list the ports you have listening and what service they are tied to.
also since you installed and configured firestarter, you now Do have a firewall in your way, (you didn;t previously) so you will have to allow the port through the firewall in firestarter.

---

### Post by Irony on 2010-08-04
> **Raymond2201 said:**
> Is that a typo? should that not read Windows? hehe
Err yes, that is correct all ports are open by default on Ubuntu - thus you use your router to set the ports.

You can run gufw to deny ports from a software perspective.

---

### Post by Manifest on 2010-08-04
Whats a typo?
```
root@-laptop:~# netstat -tulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      807/sshd        
tcp        0      0 localhost:ipp           *:*                     LISTEN      1139/cupsd      
tcp6       0      0 [::]:www                [::]:*                  LISTEN      1195/apache2    
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      807/sshd        
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      1139/cupsd      
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN      799/smbd        
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN      799/smbd        
udp        0      0 *:51381                 *:*                                 884/avahi-daemon: r
udp        0      0 *:bootpc                *:*                                 1542/dhclient   
udp        0      0 *:mdns                  *:*                                 884/avahi-daemon: r
udp        0      0 :netbios-ns *:*                                 1807/nmbd       
udp        0      0 *:netbios-ns            *:*                                 1807/nmbd       
udp        0      0 -lap:netbios-dgm *:*                                 1807/nmbd       
udp        0      0 *:netbios-dgm           *:*
```
It's funny how free software has the best support:D

---

### Post by endotherm on 2010-08-04
> **Manifest said:**
> Whats a typo?
```
root@-laptop:~# netstat -tulp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      807/sshd        
tcp        0      0 localhost:ipp           *:*                     LISTEN      1139/cupsd      
tcp6       0      0 [::]:www                [::]:*                  LISTEN      1195/apache2    
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      807/sshd        
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      1139/cupsd      
tcp6       0      0 [::]:microsoft-ds       [::]:*                  LISTEN      799/smbd        
tcp6       0      0 [::]:netbios-ssn        [::]:*                  LISTEN      799/smbd        
udp        0      0 *:51381                 *:*                                 884/avahi-daemon: r
udp        0      0 *:bootpc                *:*                                 1542/dhclient   
udp        0      0 *:mdns                  *:*                                 884/avahi-daemon: r
udp        0      0 :netbios-ns *:*                                 1807/nmbd       
udp        0      0 *:netbios-ns            *:*                                 1807/nmbd       
udp        0      0 -lap:netbios-dgm *:*                                 1807/nmbd       
udp        0      0 *:netbios-dgm           *:*
```It's funny how free software has the best support:D


ok, each of the lines here are an application listening on a port. notice that you don't have a line for port 21/FTP so that is why the port was closed to telnet. if you try the telnet again, this time targeting port 807 for instance, you should be able to connect. 
as I said, once you install and configure firestarter, you are likely now blocking ports on your system, so you will have to allow them through firestarter. here is a how to on configuring firestarter:
[http://www.techotopia.com/index.php/Using_Firestarter_to_Configure_an_Ubuntu_Linux_Firewall](http://www.techotopia.com/index.php/Using_Firestarter_to_Configure_an_Ubuntu_Linux_Firewall)

if you run the telnet query agains 127.0.0.1 it should succeed even with the firewall in place, but you will be denied by the firewall if you query the hosts network ip address, until you allow the port in the firewall

btw, 'typo' is short for 'Typographical error', like when i type 'teh' when I mean 'the'.

---

### Post by The Cog on 2010-08-04
> **Irony said:**
> Err yes, that is correct all ports are open by default on Ubuntu - thus you use your router to set the ports.
No that's not right. All ports are closed by default on Ubuntu. You can confirm this by scanning the computer from another one with nmap, or with that GRC shields up web site if you're not behind a NAT router. Or you can just try to connect to that port with telnet, e.g. **telnet 1.2.3.4 80** to check port 80 on computer 1.2.3.4. If the port is open, you get a "Connected to..." message, and if the port is closed you get "Connection refused". You open ports by starting a server program that listens for connections to that port. For instance, port 80 gets opened when you install and start a web server. Stopping the server closes the port again.

You can use a firewall program to configure iptables to deny access to ports, in which case callers will get no response when they try to connect, neither connected nor refused. Eventually they will get a timeout trying to connect, in which case they cannot tell if the port is open or closed. GRC calls this denying access by the firewall "stealthed" and they try to tell you this is somehow more secure than closed, but that's because they want to sell windows firewall software.

---

### Post by Manifest on 2010-08-05
Here's firestarter
[IMG]http://tinypic.com/r/2h3sc5j/4[/IMG]

and when I try to connect
[IMG]http://i34.tinypic.com/2wqzpn6.png[/IMG]
[IMG]http://tinypic.com/r/2wqzpn6/4[/IMG]

---

### Post by endotherm on 2010-08-05
unless you installed ftp since running that netstat output you displayed above, the issue is that you are not running an ftp server. 
if you were, you would see a line in your netstat like this:
```
tcp        0      0 *:ftp                   *:*                     LISTEN      21/ftpd
```since you don't have a ftp server daemon running, your problem is not with open/closed/stealthed/filtered/allowed/blocked ports (btw each of those means something differant, and folks are confusing the terminology a bit in this thread).

try reinstalling/reconfiguring your ftp server and see if it attaches ftpd to your TCP/21 port.

---

### Post by endotherm on 2010-08-05
> **The Cog said:**
> No that's not right. All ports are closed by default on Ubuntu. You can confirm this by scanning the computer from another one with nmap, or with that GRC shields up web site if you're not behind a NAT router. Or you can just try to connect to that port with telnet, e.g. **telnet 1.2.3.4 80** to check port 80 on computer 1.2.3.4. If the port is open, you get a "Connected to..." message, and if the port is closed you get "Connection refused". You open ports by starting a server program that listens for connections to that port. For instance, port 80 gets opened when you install and start a web server. Stopping the server closes the port again.

You can use a firewall program to configure iptables to deny access to ports, in which case callers will get no response when they try to connect, neither connected nor refused. Eventually they will get a timeout trying to connect, in which case they cannot tell if the port is open or closed. GRC calls this denying access by the firewall "stealthed" and they try to tell you this is somehow more secure than closed, but that's because they want to sell windows firewall software.


Edit: upon rereading, it seems your terminology is dead on. sorry for my presumption. regardless these definitions may help others so read on...
I think the issue here may be one of terminology:
Open  => a process is listening on the port
Closed => no process is listening on that port
allowed => port is accessible through a firewall
blocked => port is not accessible through a firewall
filtered => port is open, but access is restricted to machines with specific criteria (like localhost only)
stealthed => port is open but the input to it is sunk to null, so that no response to teh query is sent. 

by default all ports on ubuntu are closed but are allowed by the firewall. once you install firestarter you now have all closed ports that are also blocked. if you install a server with a listener port, you will have an open port, but it will still be blocked by the firewall unless allowed in firestarter/gufw

either way, I think we have confirmed that the ops issue is not firewalling or the opening or closing of ports, but that ftpd does not appear to be running.

---

### Post by Manifest on 2010-08-05
So how do I set up an ftp server Be More Specific!;)
EDIT: Yay i've got somewhere I can block ports in firestarter that are already open(Sigh) but adding ports to open dosnt work

---

### Post by The Cog on 2010-08-05
> **endotherm said:**
> Edit: upon rereading, it seems your terminology is dead on. sorry for my presumption. regardless these definitions may help others so read on...
I think the issue here may be one of terminology:
Open  => a process is listening on the port
Closed => no process is listening on that port
allowed => port is accessible through a firewall
blocked => port is not accessible through a firewall
filtered => port is open, but access is restricted to machines with specific criteria (like localhost only)
stealthed => port is open but the input to it is sunk to null, so that no response to teh query is sent. 

Sorry to be pedantic, but I would lump "filtered" and "stealthed" in with blocked - they are all words used to say the firewall is dropping the packets. As such, you cannot tell if the port is actually open or closed because you can't talk to it to get a response. Personally I dislike the word "stealthed" as meaningless salesman talk. "Filtered" might imply that the firewall is being selective about what it blocks and what it allows (different caller IP addresses maybe) but either way, the packet will ultimately either be blocked or allowed.> 
By default all ports on ubuntu are closed but are allowed by the firewall. Once you install firestarter you now have all closed ports that are also blocked. if you install a server with a listener port, you will have an open port, but it will still be blocked by the firewall unless allowed in firestarter/gufw

Now that is nicely put.

@Manifest:
vsftpd is an FTP server package in the Ubuntu repositories. From the menu, System->Administration->Synaptic and search for vsftpd, mark it for install and apply. Or from, the command line: **sudo apt-get install vsftpd**. I have no idea how to configure it.

---

### Post by Manifest on 2010-08-05
:confused: When I installed vsftpd it opened port 20-21
How do I open ports like that firestarter simply dosn't work:(
Please dont send me in another wild g00se chase
To put it bluntly.How do I open a port as simply as installing vsftpd

---

### Post by The Cog on 2010-08-05
You are confusing two separate things.

Opening a port is something that an application like an FTP or web server does when it starts. An open port is one that has an application attached to it listening for incoming connections. A closed port is one that has not been opened by a server that wants to listen for incoming connections. All ports are closed until a server process opens them.

The reason that ports 20 and 21 were closed (and therefore refused connections) is that no server was listening on those ports. When you installed vsftpd it automatically started running (the installer also starts it up). Being an FTP server, it promptly opens the standard FTP ports 20 and 21 and listens for incoming connections.

The only thing that firestarter or any other firewall has to do with this is that a firewall can prevent people even being able to talk to ports by discarding incoming connection requests. If the firewall does this, you can't tell if the port is open or closed - you just get a timeout (meaning no response received) when you try to connect. A firewall cannot either open or close a port, it can choose to block access to it or can choose to allow connections through to it. 

To be able to connect to a port therefore, 
1: There must be a service listening on that port, and 
2: Any firewall must be configured to accept/allow connections to it. 
Since a default Ubuntu install has firewall rules that permit everything, item 2 doesn't apply and the only thing you have to worry about is item 1. This boils down to: If you want to connect to an FTP server, then you have to install an FTP server first.

There are a number of people who will tell you that to open a port, you must install a firewall. This is a wild goose chase. A firewall's job is to block connection attempts whether the port is open or not. If you install a firewall there are then two things you have to do - you still have to install the service, but you also undo the blocking that the firewall is doing before you can reach it.

---

### Post by Manifest on 2010-08-06
Thank You!
But one more question does this mean the ports I open are limited to the repositories:?:

---

### Post by The Cog on 2010-08-06
No. You will find that the vast majority of software you want to install is already packaged into the repositories, and they should always be the first place you look for software. But if the repositories don't have what you're looking for, or have out-of-date versions, you are free to look elsewhere. Be cautious downloading from other web sites, some downloads are laced with malware, spyware, viruses etc.

You open ports by running server programs. The above goes for server programs as much as for any other type of software.

---

### Post by Manifest on 2010-08-06
> No. You will find that the vast majority of software you want to install is already packaged into the repositories
So that's a 'yes' then.

---

### Post by endotherm on 2010-08-06
> **Manifest said:**
> So that's a 'yes' then.
no it isn't. ports and repositories have almost nothing to do with eachother. 

the repositories hold applications and make them available to us for install. 

an installed application (installed via the repos, or **any** other method) that uses ports to listen for incoming connections will open it's own port. the port opens when the program is launched. you do not need to do anything except make sure your program is launched to open the port. 

once the port is open, it may still be blocked by the firewall, so you use firestarter to allow connections to that port.

---

### Post by The Cog on 2010-08-07
> **Manifest said:**
> So that's a 'yes' then.

No, it's a no. Read it again. The first word has two letters in it, not three. And they're different shapes - that matters.

---

