---
title: "Internet connection sharing: tutorial doesn't make sense?"
date: 2010-02-05
forum: General Help
---

### Post by t0p on 2010-02-05
At home I'm currently running Hardy on a desktop machine and Jaunty (Eeebuntu) on an EeePC.  I often connect the desktop to the internet via a cellphone as modem.  I also often connect the EeePC to the desktop via crossover cable and SSH into the desktop so I cam watch video files from the desktop on the EeePC from the sofa or bed.

I'd like to be able to use the desktop's internet connection from the EeePC.  This means I have to set up the desktop so the EeePC can share its connection - this involves setting up the desktop as a gateway I believe?

Looking around for info on how to do this, I found this guide - [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html) - but unfortunately it seems this guide has not been written correctly.  It repeats itself in one section (below: repeated section in bold):

> 
[b]Start by configuring the network card that interfaces to the other  computers on you network
# ifconfig ethX ip
where ethX is  the network card and ip is your desired server ip address (Usually  192.168.0.1 is used)
Then configure the NAT as follows
#  iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
where ethX is  the network card that the Internet is coming from
# echo 1 >  /proc/sys/net/ipv4/ip_forward[/b]
Install dnsmasq and ipmasq using the  following command
# apt-get install dnsmasq ipmasq
Restart  dnsmasq using the following command
# /etc/init.d/dnsmasq restart
Reconfigure  ipmasq to start after networking has been started
#  dpkg-reconfigure ipmasq
[b]Start by configuring the network card that  interfaces to the other computers on you network
# ifconfig ethX  ip
where ethX is the network card and ip is your desired server ip  address (Usually 192.168.0.1 is used)
Then configure the NAT as  follows
# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
where  ethX is the network card that the Internet is coming from
# echo 1  > /proc/sys/net/ipv4/ip_forward[/b]
Add the line  “net.ipv4.ip_forward = 1&#8243; to /etc/sysctl.conf
# gedit  /etc/sysctl.conf
Reboot your system is optional.


See what I mean?  What do I need to do?  Just perform the repeated section once, and follow the rest in sequence, just missing out the repeated bit?  Or is there more to it?

Cheers.

---

### Post by plucky on 2010-02-05
> See what I mean? What do I need to do? Just perform the repeated section once, and follow the rest in sequence, just missing out the repeated bit? Or is there more to it?

Cheers. 


That was probably just copied from [http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing) 


Good Luck

---

### Post by t0p on 2010-02-05
> **plucky said:**
> That was probably just copied from [http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=connection+sharing) 


Ah yes.  And in that post, step 6 is "repeat steps 1 and 2".  So that repeat in the guide I referred to at the start is not a mistake.  Now I know, I can get busy trying it out.

However, looking at that thread I can see it was written in 2005.  I hope it isn't out-dated in newer versions of Ubuntu...

---

