---
title: "Can't SSH from outside LAN :("
date: 2012-02-29
forum: General Help
---

### Post by omgitsalan on 2012-02-29
Hello everyone, i'm trying to setup a SSH server on my dektop, i've got the service running and have forwarded port 22 to my box (i also geave it a static ip from my router).

I can connect via localhost or using my LAN IP (192.168.x.y), but when i try to connect from outside or using my outside IP, i get a time out. I've tried doing it from my laptop, tablet and the very same desktop.

What I find weird is i got it to connect from a WebSSH client (Serfish).

Any idea?

Thanks a lot!

---

### Post by Pilot6 on 2012-02-29
Ypu need to allow 22 port in firewall (iptables).

---

### Post by surfer on 2012-02-29
```
$ ssh -v user@host
```
can sometimes give useful debug comments.

---

### Post by omgitsalan on 2012-02-29
I think I've made an exception in iptables, here's the output of iptables -L

```
alan@Yggdrasil:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination         

```

Also output of ssh -vvv

```
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 187.162.162.62 [187.162.162.62] port 22.
debug1: connect to address 187.162.162.62 port 22: Connection timed out
ssh: connect to host 187.162.162.62 port 22: Connection timed out

```

I've also made sure that ufw is disabled, after running nmap i ended up with this:

```

Starting Nmap 5.21 ( http://nmap.org ) at 2012-02-29 14:49 CST
Nmap scan report for 187-162-162-62.static.axtel.net (187.162.162.62)
Host is up (0.0051s latency).
Not shown: 993 closed ports
PORT      STATE    SERVICE
22/tcp    filtered ssh
23/tcp    filtered telnet
53/tcp    open     domain
80/tcp    open     http
7001/tcp  open     afs3-callback
7002/tcp  open     afs3-prserver
49152/tcp open     unknown

Nmap done: 1 IP address (1 host up) scanned in 2.54 seconds

```

I've also forwarded port 22 on router.

Why is the port filtered?

---

### Post by matt_symes on 2012-02-29
Hi

Is your ISP blocking the port ?

Check with

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

If it is blocked by your ISP then try changing the SSH port number. That is a good idea anyway as you will see less cruft in your log files.

I hope you are using keys.

Kind regards

---

### Post by omgitsalan on 2012-02-29
No, apparently my ISP isn't blocking the port, canyouseemee.org says it can see port 22.

I intend to setup keys as soon as i get this working, thanks for your concern.

---

### Post by matt_symes on 2012-02-29
Hi

I flashed my router with dd-wrt. 

I had to reboot my router before i could connect from my external IP address or my dyndns domain name. No amount of stopping and starting services would fix it until the reboot.

It's worth a try.

Kind regards

---

### Post by omgitsalan on 2012-02-29
I rebooted router and saw no change /: it's running stock firmware and i don't think i will flash it.

Thanks for all your help!

---

### Post by matt_symes on 2012-02-29
Hi

> 22/tcp    filtered ssh

This, of course, is your problem. What is the make and model of your router ? 

Someone here may have the same router as you.

Kind regards

---

### Post by omgitsalan on 2012-02-29
My router is a Zhone 2516.

Again, thanks for your help.

---

### Post by imachavel on 2012-02-29
There must be over a hundred ip terminal commands to use from Ubuntu huh? Some show ip table, others show network statistics. Don't know much about sash, except that it's a great way to log into a DNA Internet server domain to ls and view ftpd files. So how did you set up a server? Which OS is installed. Remember samba is neede to share a windows and Linux network connection. Are you using server 2008 dc promo or Linux vi?

Your subnet mask and default gateway is set up on the router. Ip protocol(dhcp or Internet dns, assume this is an internal LAN as you didn't mention VLAN VPN connection) anyway that's all done on the server. 

Ok to open port you need port number and port rule as well as specify if it's UDP or TCP. What ip is the server? You entered the ip number of server when you set up the port rule right? 

You seem to know a lot more about this then I do, I'm more referencing for myself actually. Can you ping well, how about rdp, rdp :3389, I'm not sure if it's rdp (pcname):3389 or rdp ipaddress:3389. Im pretty sure you rdp with the ip address as what can verify and translate the Mac address to computer name if you haven't established the remote connection. Well good luck, awesome thread

---

### Post by imachavel on 2012-02-29
Sorry disregard, I didn't read, you said the ip is 187.162.162.62. So class C you've got 255.255.0.0 subnet mask? Sorry I forgot cidr lol **** it that can't help your current connection problem. Ssh - vvv gives you output of connection configuration? Not much of a way to test ssh is it? Doesn't do any type of ssh specified ping or trace route does it?

---

### Post by omgitsalan on 2012-02-29
Hello, thanks for your kind words q:

The ssh server i'm running is of course openssh, and operating system is not an issue (as far as I know), I've had servers running ssh services and accesed them from within that same network using putty in windows and ssh from linux terminal.

I still haven't resolved this issue, but I'll keep working on it, thanks to everyone for their suggestions and I'm open to hearing more.

I'll keep you guys posted...

---

### Post by imachavel on 2012-02-29
Open ssh huh? How well was your previous luck using windows putty?? I wish I knew more about this stuff. Anyway you can take a screen shot of all the open ports in your router? Any differences in configuration between your previous windows putty configuration and your Linux one?? To log in its

Ssh username@ipadresss

Then it asks for a password correct?? 

Or ssh username@urladdress correct??

But there are more command line tags for ash usage I'm pretty sure

---

### Post by omgitsalan on 2012-02-29
Well the difference here is that previously i had a server running ssh and id connect to it from Linux or using putty from LAN. Now i'm trying to connect to a box from outside the LAN, the connection works properly using my desktops local address, but not my outside address. I've already posted my open ports, and apparently port 22 is not open nor closed but filtered. I think this is my problem but have yet to find out how to fix this.

---

### Post by jerome1232 on 2012-02-29
I just wanted to clarify, you have tried connecting from a box that is actually outside your lan? I ask because I have ran into routers in the past that will not allow a host inside the network, open a connection to the public ip.


ie pretend routers wan ip is 10, your servers ip is 2 and your client is 3, external box is 40.

Some routers will not allow connections from 2 or 3 to 10, but 2 to 3 is fine obviously, 40 to 10 will work as expected.

I suspect that since you said a web based ssh works (outside your lan) when connections from within your lan to the public ip do not.

I know you said your isp doesn't filter port 22, but you have tried using a non standard port just to try? (like 2222, or another very high port?)

Just taking some stabs in the dark here.

---

### Post by omgitsalan on 2012-02-29
I thought of that a while ago, the router not letting me connect from inside, but haven't had a chance to test it out, i'll do it tomorrow from a school.

If that doesn't work i'll try on another port.

Thanks for your help!

---

### Post by omgitsalan on 2012-03-01
It works! It was just as jerome1232 said, using my outside IP didn't work from inside LAN but it works beautifully from outside.

Thanks you everyone for your kind help!

---

