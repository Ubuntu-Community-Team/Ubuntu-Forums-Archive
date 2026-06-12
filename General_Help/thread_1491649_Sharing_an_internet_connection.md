---
title: "Sharing an internet connection"
date: 2010-05-23
forum: General Help
---

### Post by metaltroubador on 2010-05-23
Ok here is the problem, when I ask how to share an internet connection I get led here

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

And once I get there I'm given these steps to follow:

---------------------------------------------------------------------------

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!

--------------------------------------------------------------------------------------

However I believe this advice to be quite dated because one of the packages that you are instructed to get in Step 4 is apparently either no longer available or unusable because when I use "apt-get install ipmasq" I either get that package has no installation file or this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I tried to get help on that thread, but it appears as if that thread is more for reference now, and there's really no one there to help anymore. So I figured I'd ask for help.  Can anyone offer any assistance, please?

---

### Post by sylvester_0 on 2010-05-23
Those instructions are from 2005. See [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

> You will need either two Ethernet ports, one for the incoming internet and 1 for the connection to the other computer, or a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer. When logged into your computer right click on the network indicator in the top right hand corner, click on "Edit Connections..." select "Auto Eth0" and click "Edit..." then go to the "IPv4 Settings" tab and next to "Method:" select the drop down box and select the option that says "Shared to other computers". Restart your computer and then you will be able to just plug-in any computer to your Ethernet port to share the connection.

---

### Post by wojox on 2010-05-23
Close any other package managers that's you get that error. You can't have Synaptic or Software Center open at the same time as installing from the terminal. And you need sudo for that.

Nevermind Sylvester_0 has a better idea.

That is an old howto your using for apt-get install ipmasq

---

