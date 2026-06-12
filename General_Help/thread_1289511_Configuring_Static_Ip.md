---
title: "Configuring Static Ip"
date: 2009-10-12
forum: General Help
---

### Post by crosstalk on 2009-10-12
I have been using Ubuntu for a couple months now, and have tried to setup SSH.

For the port forwarding (it's a Netgear router) to work, however, I need a static IP address.

I found an easy tutorial online, [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html,]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") and used it. However, upon running ifconfig I found I had no IPv4 address and could no longer connect.

I never got an IPv4 address, and I also found out (searching with another computer) that NetworkManager interferes with configuration via the /etc/network/interfaces file. After removing that, I have finally reset it to:
```
auto eth0
iface eth0 inet dhcp
```and my internet worked, but I am still on dynamic IP. Also, is there some way to get the DNS servers with DHCP?

I am asking:
1) How do I configure Ubuntu for a static IP address?
2) How do I fill out /etc/resolv.conf? Is there a way to get only the DNS server via DHCP, and if not, how do I find the preferred DNS server?

Thank you for your help.

---

### Post by jeremyswalker on 2009-10-12
If you are running with a GUI, just right click on the Network Manager applet in the system tray and click "Edit Connections". Once open, select your network and click "Edit". Once open, click the "IPv4" tab. All of this configuration can be handled right there. Click "Apply" when you are done. You may have to restart your networking if it did not automatically.

---

### Post by crosstalk on 2009-10-12
Well, I tried that (first) and continued to try it repeatedly, but it repeatedly failed.

I did succeed in getting an IPv6 address with it (I didn't specify anything,) but all it did was kill my (IPv4) connection. I uninstalled network-manager in order to get my internet back up as-is.

I would rather use the configuration file than a GUI editor anyway.

Thank you for your help, but that method didn't work for me.

---

### Post by rb0171610 on 2009-10-12
> **crosstalk said:**
> I have been using Ubuntu for a couple months now, and have tried to setup SSH.

For the port forwarding (it's a Netgear router) to work, however, I need a static IP address.

I found an easy tutorial online, [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html,]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html") and used it. However, upon running ifconfig I found I had no IPv4 address and could no longer connect.

I never got an IPv4 address, and I also found out (searching with another computer) that NetworkManager interferes with configuration via the /etc/network/interfaces file. After removing that, I have finally reset it to:
```
auto eth0
iface eth0 inet dhcp
```and my internet worked, but I am still on dynamic IP. Also, is there some way to get the DNS servers with DHCP?

I am asking:
1) How do I configure Ubuntu for a static IP address?
2) How do I fill out /etc/resolv.conf? Is there a way to get only the DNS server via DHCP, and if not, how do I find the preferred DNS server?

Thank you for your help.
How do you connect to the router? Does the router assign you this IP address every time?  Meaning, does your router acts as a DHCP server and assigns the same IP address to your hostcomputer every time? If not, changing settings in your /etc/network/interfaces file would cause you not to have an internet connection.

---

### Post by jeremyswalker on 2009-10-12
If you prefer to use the configuration files, I would be curious to see what configuration you used in your /etc/network/interfaces and /etc/resolv.conf files. I looked at the link you provided. If you followed it correctly, there should be no reason why it didn't work.


Also, did you try to stop Network Manager and restart networking to see if that solved your problem?
```
sudo /etc/init.d/NetworkManager stop
sudo /etc/init.d/networking restart
```

---

### Post by rb0171610 on 2009-10-12
> **crosstalk said:**
> Well, I tried that (first) and continued to try it repeatedly, but it repeatedly failed.

I did succeed in getting an IPv6 address with it (I didn't specify anything,) but all it did was kill my (IPv4) connection. I uninstalled network-manager in order to get my internet back up as-is.

I would rather use the configuration file than a GUI editor anyway.

Thank you for your help, but that method didn't work for me.

I do not use GUI configuration utilities either. I manage my wireless connections through my /etc/network/interfaces file.  I have all of my hosts setup to get their IP from my router through DHCP. They are each set up with static IP leases.  I changed the /etc/hosts file on all computers to reflect this and their host names.

---

### Post by pricetech on 2009-10-12
The instructions look good to me also.  As far as DNS servers go, your netgear router should function as a DNS server for the internal network just fine.  If you want to add (or replace) DNS servers, log in to your router and see what your ISP is handing out to you on the WAN side and use those servers.

Another option is to set your router to always hand out the same IP to your computer based upon its MAC address.  Routers vary, but you should be able to find the setting in your router's configuration.

---

### Post by crosstalk on 2009-10-12
While I was waiting for more replies (since I didn't want to do any more work with configuration until I really knew what I was doing,) I dug deeply through every page of the router configuration (which wasn't that complex) and found a setting I had missed on every single search before (I had looked at least half a dozen times through every single page on the router.)

I was able to set it to reserve the IP address I wanted for my computer. I then rebooted my network interface and checked, and, yes, I was at the correct IP.

They should make this a little more obvious.

Thank you for all your help, but I just got it solved with my router's configuration.

---

### Post by rb0171610 on 2009-10-12
> **crosstalk said:**
> While I was waiting for more replies (since I didn't want to do any more work with configuration until I really knew what I was doing,) I dug deeply through every page of the router configuration (which wasn't that complex) and found a setting I had missed on every single search before (I had looked at least half a dozen times through every single page on the router.)

I was able to set it to reserve the IP address I wanted for my computer. I then rebooted my network interface and checked, and, yes, I was at the correct IP.

They should make this a little more obvious.

Thank you for all your help, but I just got it solved with my router's configuration.

Congratulations on your success.  I figured it should have been that easy all along. Now you can just edit the /etc/hosts file on every computer to add a line with IP address followed by hostname. Restart networking from the command line. This will reload your hosts file.  You will now be able to use ssh with the host name rather than the IP address.

*ssh hostname-of-computer*
Good Luck.

---

