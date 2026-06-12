---
title: "How do I reconnect to the Internet after uninstalling Network Manager"
date: 2009-10-08
forum: General Help
---

### Post by ozguitarplayer on 2009-10-08
Hi,
I'm trying to home network 2 Hardy Heron, 1 Jaunty Jackalope and I Debian computers on a peer to peer basis.
All works well except for making the IP's static. Every morning when I reboot the order of IP addresses changes, and all indicators show that Network Manager should be uninstalled to overcome this. 
I have tried this and when I do I loose internet connection and the only way to reconnect is to reinstall Network Manager.
I must be missing something.
How do I connect to the internet without using Network Manager?

---

### Post by StuartN on 2009-10-08
> **ozguitarplayer said:**
> Every morning when I reboot the order of IP addresses changes, and all indicators show that Network Manager should be uninstalled to overcome this.

You can assign a fixed IP address in Network Manager, or use host names instead of IP addresses to refer to your machines.

---

### Post by brukutu on 2009-10-08
wireless or wired? 
wired: 
sudo nano /etc/networking/interfaces

shud be something like
auto eth0
iface eth0 inet static
        address 192.168.16.5
        netmask 255.255.255.0
        network 192.168.16.0
        broadcast 192.168.16.255
        gateway 192.168.16.7
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.16.7

wireless:
use a program called netcfg

---

### Post by ozguitarplayer on 2009-10-08
> You can assign a fixed IP address in Network Manager, or use host names instead of IP addresses to refer to your machines.
StuartN is online now Report Post   	Reply With Quote

When I assign a fixed address in Network Manager (I am using System > Administration > Network which brings up Network Settings) and then close and reopen Network Settings it has reverted back to 'Roaming Mode Enabled'
 
Do you mean in /etc/hosts I need only enter the host name and not the IP address?

> auto eth0
iface eth0 inet static
address 192.168.16.5
netmask 255.255.255.0
network 192.168.16.0
broadcast 192.168.16.255
gateway 192.168.16.7

Yes this is how my etc/network/interfaces reads.
Woops I did forget to mention...wired

---

### Post by StuartN on 2009-10-09
> **ozguitarplayer said:**
> When I assign a fixed address in Network Manager (I am using System > Administration > Network which brings up Network Settings) and then close and reopen Network Settings it has reverted back to 'Roaming Mode Enabled'

Sorry, you are right, there is a bug in Network Manager - [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

On your other question, the host name can be used in most situations where an IP address can be used, such as shares. In many situations the IP address would be unknown to users and changes in IP address would not affect them.

---

### Post by ozguitarplayer on 2009-10-11
The bottom line is that (unless I'm doing something really daft and it wouldn't be the first time) internet connection is lost when I uninstall Network-Manager.

Surely there is a way to connect to the internet/network without Network-Manager?

On my Hardy Heron computer there is Network Settings where I can configure a static address however when I fill out the information and shut it down then re-open it the settings have gone back to 'enable roaming mode' 
Jaunty Jackalope doesn't seem to have the same Network Settings applet.

---

### Post by dcstar on 2009-10-11
> **ozguitarplayer said:**
> 
.........
How do I connect to the internet without using Network Manager?

Install the **gnome-network-admin** package and configure your network using that.

Network Manager is a POS IMHO - anything that is that brain-dead to require to log in before networking actually functions should be shot.

---

### Post by delcypher on 2009-10-11
If you have a wired connection that you manually have to set IP,netmask,gateway,dns settings for then you can do the following:

Assuming the eth0 interface is your wired card (run ifconfig to get a list of devices and their current state)
```

sudo ifconfig eth0 up #Bring up interface
sudo ifconfig eth0 192.168.16.5 # set IP address
sudo ifconfig eth0 netmask 255.255.255.0 # set subnetmask (should be set to this already)
sudo ifconfig eth0 broadcast 192.168.16.255 #set broadcast address
sudo route add default gw 192.168.16.7 eth0 #set gateway address
sudo echo nameserver 192.168.16.7 >> /etc/resolv.conf # add DNS entry to resolv.conf file - you edit manually yourself if you prefer

```

That should setup everything, if your network has a dhcp server life is much easier, just run (where eth0 is your network interface)
```
sudo dhclient eth0
```

Now once you've got your interface try pinging a few things (maybe another computer on your network and then if that's successful google.com)

---

### Post by ozguitarplayer on 2009-10-15
After weeks of trying wiith Network-Manager I finally got 4 home computers set up with static addresses using wicd.
From what I've read Network-Manager has known bug issuses with static addresses.
This link has all the info I needed to do it.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Many thanks to all who helped along the way.

---

