---
title: "networking and startup"
date: 2010-01-26
forum: General Help
---

### Post by mmmato on 2010-01-26
Hello, I'm new to this forum and to linux. I installed it today, I have set up vnc server by following commands:

sudo apt-get install x11vnc vnc-java
x11vnc -storepasswd
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800

It works, i can connect to it from my windows mashine. How do add vnc server to start-up, so it runs when system boots?

Then I set up Internet connection sharing and DHCP as shown on this link:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

This also works, but not after I reboot the mashine, I obviously have to add another line to startup for this too.

And how do I see file extensions in File browser?

---

### Post by krunge on 2010-01-26
> **mmmato said:**
> How do add vnc server to start-up, so it runs when system boots?
This is always a bit tricky because x11vnc needs to attach to an existing X server. This is easiest if you are already logged into your desktop.

However, if GDM (gnome display manager) is your login greeter, you can place the x11vnc cmd you mentioned followed by an '&' to put it in the background in a startup script; using your example:
```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800 &
``` Put that line near the bottom of the GDM startup script file named "/etc/gdm/Init/Default" (but be sure to put it before any 'exit' line in that script.)  Then after the system boots you can access the login greeter via VNC.

One heads-up, GDM is getting dumber and more broken as time goes on and so you may encounter problems:
[INDENT][http://ubuntuforums.org/showthread.php?t=1306696&highlight=x11vnc+init+default](http://ubuntuforums.org/showthread.php?t=1306696&highlight=x11vnc+init+default)[/INDENT]

Feel free to post back here if the /etc/gdm/Init/Default method doesn't work for you and I will try to help.

BTW: there is general Unix info for attaching x11vnc to a login greeter here:
[indent][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/indent]

---

### Post by mmmato on 2010-01-27
Hi, i fixed the first problem by simply using the integrated vnc server with GUI. Now I am having problems with ICS and dhcp.

eth1 = the network adapter with internet (external or WAN).
eth0 = the network adapter to which an acces point is connected 
192.168.0.x = IP subnet for eth0

I wrote this script:

sudo ifconfig eth0 192.168.0.1
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
sudo /etc/init.d/dnsmasq start

as it is shown in the link in my first post, i also had to edit two config files. It works fine, and to start it at boot I did this:

I saved my script in /etc/init.d/ and run
sudo update-rc.d myscript defaults
sudo chmod +x myscript

The problem now is, that the script actually runson boot, but DHCP works only for a few seconds, then another process overruns the first line (where IP is set) and looses the IP. It is probably the connection manager. Somehow I need to stop it from messing with eth0, but it still has to get an ip on eth1 (WAN dynamic IP).

---

