---
title: "SSH connection refused"
date: 2011-04-01
forum: General Help
---

### Post by FerretWithASpork on 2011-04-01
Hey guys,

I've got 2 laptops both running Ubuntu (one 10.04, the other 10.10), and I'm trying to SSH from one to the other but am having no success. Here's what I've done so far:

*Installed openssh-client && openssh-server on both machines
*Opened port 22 on the remote machine via Firestarter
[S]*Forwarded port 22 on my router to the remote machine's IP (192.168.1.3)[/S]
(deleted the port forward)
*Added my user account to the "ssh" group on the remote machine

And still when I try to ssh into it I get Connection Refused.

Any ideas?

---

### Post by WinterMadness on 2011-04-01
you dont need to port forward anything if its on the same network. Judging by the fact that the ip youre using is 192.168.1.3 means its on your network (if that confused you, you should learn the difference between public and private ips, and read a bit about subnetting). You only need to port forward it when you want people from the internet to be able to connect to it.

Make sure that when you installed openSSH server that its actually running and in a listening state.

try port scanning 192.168.1.3. If you're using gnome, it comes with a handy utility called Networking Tools in the system>admin section I think.

(Id recommend nmap though, but its no hurry honestly)

If you dont see port 22, then the server isnt running or a firewall is blocking it.

---

### Post by lithopsian on 2011-04-01
Check /var/log/auth/log on the remote machine to see if connections are being detected and rejected.  Then check /etc/ssh/sshd_config to see if the right port is being listened, your IP allowed, etc.

Don't forward port 22 unless you have to.  That will allow remote access to your machine and you don't want that.

---

### Post by FerretWithASpork on 2011-04-01
I ran a port scan on the remote host (192.168.1.3) on both computers. When I ran it on the remote host it says that port 22 is open, but when I scan from the local host (192.168.1.2) it couldn't find anything.

After further investigation I opened up firestarter and it was blocking the scan attempts, so I added a policy to allow connections from 192.168.1.2 and ran the scan again, it took forever but it did find port 22 as open.

This seems to have fixed the Connection Refused problem, but now I'm getting Connection Timed Out.

---

### Post by lithopsian on 2011-04-01
Connection timed out would suggest that the remote server is not listening for your request, or the request is getting sent to the wrong place.  Check the log.

---

### Post by FerretWithASpork on 2011-04-01
So I found out that I can ssh into it if I use the WAN IP, but not using the hostname, any way to fix this?

---

### Post by newbuntuxx on 2011-04-01
1. Can you post the private IP addresses of both of your computers.

2. Are they both connect to the same router?

3. On each computer, try to ssh to itself like this:

```
ssh username@localhost
```

Does that work?

4. Run a tcpdump like this on one computer A:

```
sudo tcpdump -i any port 22
```

Then try to ssh from computer B to computer A. Does the tcpdump output anything? if yes, copy and paste it here.


5. Disable firestarter on both computers (because firestarter blocks outgoing and incoming traffic) and then try to ssh from A to B and vice versa. 
 
For future reference, when you want to enable an ssh server on an Ubuntu desktop machine, you simply have to install the openssh-server like this:

```
sudo apt-get install openssh-server
```

And thats it! You don't need to do anything else to setup the server. Everything will work. When you attempt to login to the remote machine via ssh, you need to use a user name that exists on the remote machine.

As for your router, note that you have five ports on it, 1 external and 4 internal (you may also have a wireless transceiver). Any computers/devices connected to the internal ports/wireless transceiver are considered to be on the same subnet (local network). These devices can talk to each other freely without any inspection/filtering done by the router. The only traffic that is filtered/inspected is traffic coming in from the external router.

Hope this helps

---

### Post by WinterMadness on 2011-04-01
> **FerretWithASpork said:**
> So I found out that I can ssh into it if I use the WAN IP, but not using the hostname, any way to fix this?

remove the port forwarding you did.

---

### Post by newbuntuxx on 2011-04-01
Forgot to reply to your "hostname" question.

You must add the hostname/ip address to your hosts file on each machine. The hosts file is in /etc/. Its called: hosts

```
cd /etc/
sudo nano hosts

```

At the bottom of that file, add the ip address, then tab, then the corresponding host name like this:
```

x.x.x.x    hostname

```

So, you would add the IP address/host name of computer A in the hosts file on computer B, and vice versa. That way, you can use the hostname to ssh.

---

