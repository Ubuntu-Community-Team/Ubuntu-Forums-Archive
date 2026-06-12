---
title: "Can ssh from many clients but not from one..."
date: 2011-01-17
forum: General Help
---

### Post by steevven1 on 2011-01-17
So I have had an ssh server set up for a long time, and it has worked with ALL my clients for a long time without problems, and suddenly I can only ssh from ONE of the clients (my laptop) to the server some of the time. Most of the time it says "connection timed out."

Now the strange part: At the same time, this client can ssh to other servers with no problem, and if I ssh into another server, then ssh from that server to the problem server, it works every time!

Any ideas?

Thanks in advance!

---

### Post by efflandt on 2011-01-17
Is it local (private LAN IP) or through the internet?  And if to different location on the internet, does it use some sort of dynamic DNS (maybe not updating promptly enough if public IP changes)?  Or are you trying to connect with client behind a firewall that might block something?

One thing that trips some people up is trying to connect from same LAN using public name or IP, because many routers (including Linux by default) do not do LAN to LAN via public IP as a security measure against spoofing (they do not expect a LAN IP on public interface).

---

### Post by endotherm on 2011-01-17
one possibly is a known key mismatch. are you connecting via commandline, and is the only message that the connection timed out?
if so, the next question is where is the server in relation to your self? is it on your lan or on a wan link? if it;s on a wan link, try a traceroute to the target and see if you can connect at all.  if you can, but ssh still fails, try logging in from another host, and looking at the logs on the client (the messages system and kern.log ) to see if you recieved a request and dropped it or if the firewall blocked it in mid stream. do you use any filters or tools like denyhosts/fail2ban?

---

### Post by steevven1 on 2011-01-17
It is through the internet. There is a dynamic DNS for the server, but it updates every 10 minutes, and I don't have any problem connecting from other machines, so I don't think that's the problem.

I am connecting through the command line, and yes, the only output is that the connection timed out. I am sure that my key is good because it connects SOME of the time (just not most of the time). I don't know what traceroute is, but I'll try looking it up. I don't use filters/denyhosts/fail2ban.

I guess I should mention that I am connecting to a non-standard port on the server with the "-p" flag, but like I said, it has always worked before, and it does work from other machines.

Thanks for the input! Any more ideas are welcome!

---

### Post by v1nny on 2011-01-17
> sudo apt-get install traceroute
traceroute <host.dyndns.org>

It's possible, though unlikely, that there is some bad routing in the internet between you and the destination server. If that is the case, it'll likely clear up in a few hours or days.

---

### Post by steevven1 on 2011-01-17
Traceroute gave me the output:

```
 1  192.168.1.1 (192.168.1.1)  0.824 ms  1.092 ms  1.188 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

Not sure what this means. Apparently, the default setting is "30 hops max," which may correspond to the output ending at 30 lines. I'll read up on it. Still, any more comments are appreciated. Thanks!

---

### Post by steevven1 on 2011-01-17
One more thing: I just tried to ssh to a box on the LAN from my laptop (which uses the same non-standard port as my other ssh server I'm having problems with), and it also gives "connection timed out." However, ssh connections to boxes on port 22 work flawlessly from my laptop. Hmmm...

---

### Post by v1nny on 2011-01-17
> **steevven1 said:**
> One more thing: I just tried to ssh to a box on the LAN from my laptop (which uses the same non-standard port as my other ssh server I'm having problems with), and it also gives "connection timed out." However, ssh connections to boxes on port 22 work flawlessly from my laptop. Hmmm...

Sounds like you have a firewall setup, either on the local machine or somewhere on your network, that is blocking bunches of traffic (like whatever port you're using for ssh, and ICMP packets used by traceroute).

---

### Post by steevven1 on 2011-01-18
Strange since I have installed no such firewall, and I've been behind the same router for over a year now and the problem just appeared. Is there a way to make my ssh client on my laptop use a different outgoing port for ssh? Also, how does this explain the lack of problem with ssh servers running on port 22? The listening port of the server should have nothing to do with the outgoing port my laptop is using, should it?

---

### Post by endotherm on 2011-01-18
well, to me it sounds like the server is up and down, and it has just been a coincidence that it alwasy seems like it;s the laptop that has the problem. that your desktop does not work at a minimum means that the problem is tied to your site, not your laptop. that could be a firewall reacting to changes in traffic level/type/behavior, or it could be a simple DNS resolution problem, or a deeper issue with routing in your neck of the intarweb. are all the hosts at the differant sites you administer using the same DNS servers to resolve queries for the remote domain?

---

### Post by pl@yer on 2011-01-18
Are you sure that the daemon is still listening on that non standard port?
```

sudo netstat -atunop|grep -i list|grep ssh

```

---

### Post by steevven1 on 2011-01-18
I would like to discount the possibility that the server is intermittently up and down, because I have physical access to it and have checked that this is not the case.

Yes, all of the hosts I'm connecting to use the same DNS server, but even when I try to connect by specifying an ip address rather than a domain name, it times out.

Also, you may have misunderstood: The ONLY client which will not connect to my servers is my laptop. There has not been a SINGLE time-out from another client (I tried a wired desktop and another wireless Ubuntu laptop on the same network as my laptop). I am quite convinced that it is an issue with my laptop, and not my network or my server.

Does that help narrow things down? Thanks for all the help.

---

### Post by steevven1 on 2011-01-18
> **pl@yer said:**
> Are you sure that the daemon is still listening on that non standard port?
```

sudo netstat -atunop|grep -i list|grep ssh

```

Yes, I am sure (and I ran your command just to be doubly sure). Thank you for the suggestion though.

---

### Post by pl@yer on 2011-01-18
Did you try deleting the ~/.ssh/* stuff on the laptop?

Could it be iptables on the laptop blocking the outgoing connection? 
```

iptables -L

```

---

### Post by v1nny on 2011-01-18
> **steevven1 said:**
> Strange since I have installed no such firewall, and I've been behind the same router for over a year now and the problem just appeared. Is there a way to make my ssh client on my laptop use a different outgoing port for ssh? Also, how does this explain the lack of problem with ssh servers running on port 22? The listening port of the server should have nothing to do with the outgoing port my laptop is using, should it?

Firewalls can be configured to block based on destination port as well as source port. As pl@yer suggested, check your IPTABLES configuration on your laptop and remove your local ssh configuration to eliminate that as a possible problem.

> 
sudo iptables -L -v


> 
mv ~/.ssh ~/.ssh.bak


---

### Post by hawkmage on 2011-01-18
Another thing I find helpful when troubleshooting a SSH problem is to use the "-vv" option like this:
```
ssh -vv user@hostname
```
This will give you a lot of debugging output.  If you still do not see an error you can try using "-vvv"

---

### Post by bdhook on 2011-02-08
I am also having this type of problem. I have done quite a bit more testing, and I am almost certain it has something to do with the combination of the wifi drivers/software in Ubuntu 10.x and Cisco APs using WPA-PSK2.

My netbook, running anything from 10.04 up to the latest 11.04 beta will not connect to SSH via WiFi while on my work campus. Another similar netbook, running 9.10, connects just fine over the same WiFi network, eliminating node-isolation issues as the cause. My netbook also works just fine on SSH when using WiFi at my house on a Linksys WRT54G v2 wireless router, confirming that it isn't just the WiFi hardware/driver as the issue, and also ruling out software issues as a sole cause. I am the administrator of the WiFi on my work campus, so I know there are no blocks in place. There are no firewalls, other than local machine firewalls, between the machines. I have verified that the iptables rules are cleared on both ends, so nothing is blocking the traffic.

When I turn on verbose output in SSH, the output indicates that a connection is established, but I am never delivered to a CLI prompt.

This is a very annoying issue, and I have been forced to find a LAN cable or resort to Bluetooth DUN connectivity in order to control servers via SSH with my netbook at work.

---

