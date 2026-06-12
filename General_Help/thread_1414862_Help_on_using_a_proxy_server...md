---
title: "Help on using a proxy server.."
date: 2010-02-24
forum: General Help
---

### Post by karthick87 on 2010-02-24
I have been using squid for a couple of months in a single PC..And it works fine for me..The only problem is if i disable the proxy settings in my browser it bypasses the rules and therefore no restrictions are applied..I want to force my browser to go through my proxy..How can i do this?I have been searching the way to do this for a longtime and i haven't got the right solution...Someone help me!! Thanks in advance

---

### Post by ndefontenay on 2010-02-24
Hi.

You have to modify your network so that any connection not using the proxy address in the web browser won't be allowed to connect to the internet since it's physically impossible.

Another way is to add the proxy to the web browser and remove the ability to modify it to your end users.

Nico

---

### Post by karthick87 on 2010-02-24
Can you give me some more information to do this?

---

### Post by ndefontenay on 2010-02-24
It's been a while. I think you can find user cases quite easily on how to configure that.

For the physical model, you'll need a server with 2 NICs. One will server your LAN and the other your WAN. 

You'll plug your internet router in one of them and a cable coming from your switch in the other. 

On that server you install squid. And from there the fun begins.
That server needs to be quite powerful too if you have many users. If you implement caching to improve speed you'll also need quite a lot of RAM.

I'm digging a little bit.

Nico

---

### Post by ndefontenay on 2010-02-24
I believe this could be of some use:

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

Nico

---

### Post by cong06 on 2010-02-24
It depends on your situation.
The best way to do it is with transparent proxying. Which just means that all the packets get redirected to the proxy without the end users knowing. This is nice if network will grow.

What I do for this is:
```

s_ip="10.42.43.1"
inet="ppp0"
lan="eth2"
s_port="3128"
iptables -F; iptables -X; iptables -t nat -F; iptables -t nat -X; iptables -t mangle -F; iptables -t mangle -X; iptables -t raw -F; iptables -t raw -X
iptables -t nat -A PREROUTING -i $lan -p tcp -m tcp --dport 80 -j DNAT --to-destination $s_ip:$s_port
iptables -t nat -A PREROUTING -i $inet -p tcp -m tcp --dport 80 -j REDIRECT --to-ports $s_port

```
(Of course modify it for your needs: Server IP, external interface, internal interface and Squid Port)

This will only redirect requests that come to 10.42.43.1. In the case that you are using the computer 10.42.43.1 requests will go straight to the internet and you'll have to do more iptables magic that I'm not quite sure about yet..

The other option mentioned though was to 'freeze firefox settings'
This is a bit confusing, and a bit messy:
[http://kirksblog.steffensenfamily.com/archives/24](http://kirksblog.steffensenfamily.com/archives/24)

---

### Post by cong06 on 2010-02-24
Oh: other things I had to do:
1) edit /etc/sysctl.conf, uncomment:
```

#net.ipv4.ip_forward=1

```
2) edit squid to add transparent as an option to my http_port
```
http_port 3128 transparent
```

The first one I'm not too sure about though.

Also I had to make the iptables confuration a script that was run each time the connection went up... because it kept clearing. I'm curious if you have to do all this also, since it seems no one else did. (maybe it's because I was using a mobile broadband connection as my outgoing?)

---

### Post by karthick87 on 2010-02-27
I am using squid in a single PC..Why should i use two NIC cards???

---

### Post by cong06 on 2010-02-27
Sorry, I made the incorrect assumption that you'd want squid to manage several computers...

I honestly don't know how to set up iptables to redirect from localhost. I'm sure google does, or another member in the forum though.

Just curious (just ignore it if you don't want to answer): why do you want squid installed for just one computer? muliple browsers? Otherwise locking your firefox plugins might be easier?

---

