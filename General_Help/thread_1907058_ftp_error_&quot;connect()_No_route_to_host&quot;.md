---
title: "ftp error &quot;connect(): No route to host&quot;"
date: 2012-01-10
forum: General Help
---

### Post by carranty on 2012-01-10
I have  a home network (no proxies) with two desktop PCs attached that I transfer files between using the ftp client yafc.  Its been working fine until I set up a static IP address on both machines.  One runs Mint 9, the other Ubuntu 10.04 (basically the same distro) and I set up the static address by using network manager (see attached screenshot).  

Everything else works fine, I can browse the web, use nmap to see other machines on the network (including the one I'm trying to connect too) etc, I just can't seem to log in via ftp.  Does anyone have any ideas why its doing this?

Below is the terminal output when I try to connect

```
carranty@carranty-desktop ~ $ yafc ftp://birbeth@192.168.0.4
yafc 1.1.1 Copyright (C) 1998-2001 Martin Hedenfalk <mhe@home.se>.
This program comes with ABSOLUTELY NO WARRANTY; for details type 'warranty'.
This is free software; type 'copyright' for details.

Connecting to 192.168.0.4 (192.168.0.4) at port 21...
connect(): No route to host
yafc> 
```

---

### Post by zero2xiii on 2012-01-10
Hay,

Did the FTP work before the static adresses. A common cause for this is the network IPs being on a diffrent subnet (i think its called) than the router, for example:

Router is 19.168.**1**.1
And then the computers is on 192.168.**0**.1 and 192.168.**0**.2

And check the route. Make sure the route is setup to go TROUGH the router (I see you did setup the gateway). Also make sure all the services are running, and the router supports the protocol on static IPs.

If it still doesn't work. Please give us more information on what servers your are using for the ftp protocol, and the outputs of:

ifconfig
route

Cherz

---

### Post by carranty on 2012-01-10
> **zero2xiii said:**
> Hay,

Did the FTP work before the static adresses. A common cause for this is the network IPs being on a diffrent subnet (i think its called) than the router, for example:

Router is 19.168.**1**.1
And then the computers is on 192.168.**0**.1 and 192.168.**0**.2

And check the route. Make sure the route is setup to go TROUGH the router. Also make sure all the services are running, and the router supports the protocol on static IPs.

Cherz

FTP worked fine before changing to static IPs, I've been using it for over a year with no difficulties. Everything is on the same subnet - router is 192.168.0.1, remote computer is 192.168.0.4 and host computer is 192.168.0.3.

How do I check to make sure route is setup to go through the router?

If the router didn't support static IPs wouldn't I be having trouble browsing the net?

> **zero2xiii said:**
> 
If it still doesn't work. Please give us more information on what  servers your are using for the ftp protocol, and the outputs of:

ifconfig
route



```
carranty@carranty-desktop ~ $ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4a:ca:1d  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe4a:ca1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7836819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4015985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2677329014 (124.3 MB)  TX bytes:351196233 (12.7 MB)
```

```
carranty@carranty-desktop ~ $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by lechien73 on 2012-01-10
What ftp server software are you using? I'd be inclined to think that the ftp server is set up to ignore specific IP's or to bind to one IP specifically.

If you run:

```
netstat -l | grep ftp
```

on the machine with the ftp server, do you get output like the following:

```
tcp     0   0 *:ftp               *:*                     LISTEN
```

---

### Post by carranty on 2012-01-10
> **lechien73 said:**
> What ftp server software are you using? I'd be inclined to think that the ftp server is set up to ignore specific IP's or to bind to one IP specifically.

If you run:

```
netstat -l | grep ftp
```on the machine with the ftp server, do you get output like the following:

```
tcp     0   0 *:ftp               *:*                     LISTEN
```

I'm not sure what ftp server sofware I'm using - its been so long since I installed it.  Is there a way I can find out?

Running the above code on the remote computer I get
```
birbeth@birbeth-desktop:~$ netstat -l | grep ftp
tcp        0      0 *:ftp                   *:*                     LISTEN    

```
exactly as you thought.

---

### Post by lechien73 on 2012-01-10
On the remote machine, if you open a terminal window and type:

```
ftp localhost
```

Do you get a welcome banner? If so, this will likely tell you what ftp server you're using.

---

### Post by carranty on 2012-01-10
> **lechien73 said:**
> On the remote machine, if you open a terminal window and type:

```
ftp localhost
```Do you get a welcome banner? If so, this will likely tell you what ftp server you're using.


```
birbeth@birbeth-desktop:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.2.2)
Name (localhost:birbeth): 
```

If I then enter the username and password

```
Name (localhost:birbeth): birbeth
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```

---

### Post by lechien73 on 2012-01-12
Sorry - I was away for a day.

You're using vsFTPd as your server, which stores its configuration details in /etc/vsftpd.conf.

Is the **listen-address** option set in that file?

---

### Post by gsgleason on 2012-01-12
Sounds like a firewall issue.

On the ftp-server, do 'sudo iptables-save' and show output here.

[edit]

Also, two hosts on the same broadcast domain and same subnet are not going to use the router to communicate.

Make sure you can ping between hosts as well.

---

