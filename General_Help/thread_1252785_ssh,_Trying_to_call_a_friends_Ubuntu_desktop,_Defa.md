---
title: "ssh, Trying to call a friends Ubuntu desktop, Default settings?"
date: 2009-08-29
forum: General Help
---

### Post by VipX1 on 2009-08-29
My friend is having trouble with vsftpd. I told him to install Openssh-Server. Set me up as a user on the desktop anding me to admin group and ssh group. He also ticked the Administrator box under my username setup. Then I got him to open port 22 on his router to his desktop i.p.
It's not connecting thought..
I use ssh myself on my web server and I'm trying to conect the same way..
ssh -p 22 user@DSL i.p. 
(my defaut port is different on my desktop set up, hence the -p 22...)

Any sugestions?

---

### Post by bear24rw on 2009-08-29
can he login with his other username over the internet?
can he login with your username from inside his lan?
maybe he isp blocks port 22?

---

### Post by bodhi.zazen on 2009-08-29
Post the output of 

ssh -vv -p 22 user@ip

I am guessing you have used

ssh -p 22 user@server ip_address ?

---

### Post by VipX1 on 2009-08-29
I'll get him to try it locally. He has a Ubuntu laptop. It should be hard to use ssh-client on that. He's bad at taking instruction though..
Maybe the router firewall is on. I'm trying that now. It's one of those problems you just have to muddle threw..
Thanks though.
It's a pain the way trying to help some one can take half the day on you..
Once I have ssh working it will be easier.

---

### Post by VipX1 on 2009-08-29
```
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to *.*.*.* port 22.
debug1: connect to address *.*.*.* port 22: Connection timed out
ssh: connect to host *.*.*.* port 22: Connection timed out

```I trying to set up a firewall rule by instruction. 
I think it is the firewall not letting threw the protocol. I'm getting him to allow my DSL to connect to all local i.p.'s on all protocols.
That's a nice command ssh -vv *
Thanks..

---

### Post by VipX1 on 2009-08-29
We have the rue set up but ... 
It's in the wrong place. It's in LAN to WAN and not WAN to LAN....
It's all good.. I would mind but I work with this guy and we work with i.t. stuff...[-o<

---

### Post by VipX1 on 2009-08-29
OK guys,
I've tried everything today. Router firewall is off. UFW is not installed on the host, no firewall is. 
vsftpd is installed and ssh is installed and configured. I can't see either service. My friend can see the ssh on his network locally but can't see vsftpd. Why can't I see ssh? I have the access to the router over the WAN and I've configured it openning NAT portforwarding to the host i.p. on port 22. The ssh_config file an the host is in the defualt state because I can't get at it...
I'm out of ideas.
P.S. remote desktop to the host times out too..
My friend has probably done something that I've not thought of that's causing the problem. What can I do about that.

---

### Post by wojox on 2009-08-29
Is Remote Login disabled in System > Admin > Login Window > Remote?

---

### Post by VipX1 on 2009-08-29
The remote desktop is set up according to my friend. He tried ssh locally and it worked. He tried it from his Ubuntu laptop. FTP access does not work locally and I didn't get him try Remote desktop log in locally cause I would have to explain how to do it.. I explained ssh and it worked locally and the FTP is what I originally was helping him with and does not work locally. As far as ssh is concerned it works locally and doesn't work over WAN. I'll look at the router again. It must be faulty..

---

### Post by jerome1232 on 2009-08-29
Did you try switching ports, his isp could be blocking port 22.

---

### Post by VipX1 on 2009-08-29
I have the Firewall on and I set up a rule to allow my DSL i.p. only to connect to his Desktop on port 22 and to keep a log of all connections. In the log it say:
No.1 - 11/08/2009 00:16:47 TCP RST My i.p. Host local i.p. port 22 Access permitted
No.2 - 11/08/2009 00:16:47 TCP RST My i.p. Host local i.p. port 22 No response (Connection timed out)

ISP is working and the firewall is active and alowing the protocol threw. The Ubuntu Desktop is not answering back...

And I can see all the feckers tring to log in and I have al the i.p.'s in the log.I will not post an i.p. ever again. It wasn't intensional, it was in the Verbose output but it's been intresting just to see how many of you exploited it..   Firewall is on and staying ON!

---

### Post by jerome1232 on 2009-08-29
lol, no those are bots trying to get in.

If you put a ssh server on port 22 it will be attempted on all day by various bots. My ssh server bans between 5-8 ip's a day. If you whois a couple I bet a good number are Chinese ip's.

---

### Post by VipX1 on 2009-08-29
Nice one.  I didn't want to whois them because then they would have my i.p. too..
A bit paranoid, I know..
Thanks.

---

### Post by VipX1 on 2009-08-29
I can see my i.p. getting threw on his firewall log. The connection from my DSL is Permitted and the router sends a TCP RST.. Then it times out. It has to be the Ubuntu desktop at his end. I can ping his local i.p. from his router. I can't get him now to talk him threw changing port but he's bad at taking instruction. We were using Skype and I told him to paste a sudo gedit command to open ssh-config in the /etc/ssh directory and he sent back the output to me..
 *bash: …: command not found*
He included the DOTS from the skype message. So what can I do.

If you don't mind me asking, if you know, what do Bots want with ssh connections on port 22. I thought they looked at web sites and thier directories and thier different pages?? What can they be hoping to find on port 22. Or is it like searching out whatever it can find, to a malicious end?

---

### Post by Phixion on 2009-08-29
Slightly off topic but proftpd is a great alternative, it works without configuration, simply FTP to your server and enter your username/pass.

---

### Post by blueridgedog on 2009-08-29
I would setup tcpdump on his PC while you are trying to connect, perhaps it will give you more information.

You can also run nmap on his public ip to see what ports are open:
```

 nmap -PNsV xxx.xxx.xxx.xxx
```

---

### Post by VipX1 on 2009-08-29
```
nmap -sT -sV -p 20,21,22,23 -T4 -n *.*.*.*

Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-30 03:07 IST

Interesting ports on *.*.*.*:
PORT   STATE    SERVICE  VERSION
20/tcp filtered ftp-data
21/tcp filtered ftp
22/tcp filtered ssh
23/tcp filtered telnet

```
I installed the user interface for nmap and then robbed the arguments from that interface and used them in the terminal nmap commandl. The interface was giving no useful output.
This means the packets are being filtered by the host firewall?? I'm not sure?
The original command you gave me had only this output..```
Starting Nmap 4.76 ( http://nmap.org ) at 2009-08-30 02:19 IST
Interesting ports on *.*.*.*:
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

```

---

### Post by VipX1 on 2009-08-30
From the Host Desktop:
```
 sudo /etc/init.d/ssh start
* Starting OpenBSD Secure Shell server sshd  
[OK ] 
kev@kev-Ubuntu:~$ sudo update-rc.d ssh defaults
 System startup links for /etc/init.d/ssh already exist.

```
From Host after reboot:
```
ssh -vv me@*.*.*.*.
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *.*.*.*
debug2: ssh_connect: needpriv 0
debug1: Connecting to *.*.*.* [*.*.*.*] port 22.
debug1: connect to address 93.107.73.117 port 22: Connection timed out
ssh: connect to host *.*.*.* port 22: Connection timed out

```From Host after the reboot.
```
 
ps -A | grep ssh
4785 ?        00:00:00 sshd
```

---

### Post by spiderbatdad on 2009-08-30
try adding his local ip to his /etc/hosts file.
127.0.0.1	his-desktop	localhost.localdomain	localhost 
xxx.xx.xx.xx
127.0.1.1	his-desktop

If this continues to fail, he might contact his isp and ask why he can't access from wan. maybe nat routing by isp is changing the actual external address.

---

### Post by VipX1 on 2009-08-30
I moved the port up to 47500 and it worked but ... Now I have to set up a Key. How do I get ssh to work without needing a key to access the remote host

---

### Post by jerome1232 on 2009-08-30
By default it accepts a password, you shouldn't need a key.

---

### Post by blueridgedog on 2009-08-30
I use keys to prevent using a password on some systems.  See here:

[http://ubuntuforums.org/showthread.php?t=1034740](http://ubuntuforums.org/showthread.php?t=1034740)

---

