---
title: "question about static ip setup"
date: 2009-09-21
forum: General Help
---

### Post by cpthk on 2009-09-21
Hi:

I just installed fresh ubuntu. I setup as static ip address. I did:

sudo vim /etc/network/interface
add:
auto eth0
iface eth0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1

then:
sudo /etc/init.d/networking restart

Everything works fine, but I realized after awhile, the internet will not work. I did ifconfig, I still have the ip address no problem. I tried to ping my router 192.168.1.1, no problem. I think the problem is dns resolve issue, because everything with ip address works fine, only with web address has problem. I did:

sudo vim /etc/resolv.conf
show:
nameserver 192.168.1.1

This has no problem too. I can't find any problem. Even I restart, the problem is still there. I really have to change back to DHCP mode to get it work, and then change back to static ip mode.

Anyone know the problem is?

Thanks.

---

### Post by denver on 2009-09-21
You could try a different resolver. Add the following to your resolv.conf:


```
nameserver 208.67.222.222
nameserver 208.67.220.220

```

These are the OpenDNS resolvers. Also, try to ping those 2 IP's and see if it works. If it does not, run this command:

```
mtr 208.67.222.222
```

and see where the trace stops.

Good luck!

---

### Post by cpthk on 2009-09-21
Is it possible to be the gnome network manager conflicts with my manual setting? I saw some people suggest to uninstall network manager. I realized the setting I set manually does not reflect on the network manager, it seems network manager has its own setting.

---

### Post by denver on 2009-09-21
Sorry, i presumed you were not using network manager :). YES....network manager has a tendancy to overwrite your changes.

If you are on a desktop system, i strongly recommend you configure your network via nm-applet (NetworkManager). It's easy, fast and flexible! Its almost a shame not to use it. Works great with my 3G modem, VPN at work, dial-up at home and wireless access point.

I have only had to mess with the interfaces file on servers. On desktops NetworkManager is the way to go :). Just right click nm-applet and go to:

Edit Connections-->Wired-->Edit

The GUI is verry intuitive. Good luck!

---

### Post by cpthk on 2009-09-26
the network manager seems doesn't save default gateway setting after reboot.

---

### Post by r.osmanov on 2009-09-26
```
broadcast 192.168.1.255 
```
is missing in your /etc/network/interfaces

Are you sure that eth0 has MAC and IP configured correctly?

About Network Manager. Personally, I had much troubles with it. 
Once I removed it with --purge and it's daemon from startup, my manual configuration began to work.

Generally, I made the following steps:
1. Stopped NM's daemon and removed it from startup
2. Removed NM package
3. Turned off interfaces (ifconfig <interface> down)
4. Put configuration into /etc/network/interfaces and /etc/resolv.conf
5. Turned on interfaces (ifconfig <interface> up)
6. sudo /etc/init.d/networking restart

NM had the only advantage for me -- network activity indication. 
Therefore, I just set System Monitor's Network indicator on Notification Area.

network-admin is a good tool also.

Good luck.

---

### Post by dcstar on 2009-09-26
> **r.osmanov said:**
> 
.......
NM had the only advantage for me -- network activity indication. 
Therefore, I just set System Monitor's Network indicator on Notification Area.

network-admin is a good tool also.

Simply install the **gnome-network-admin** package and remove the network-manager package, then reboot and reconfigue using the (old) Gnome GUI. This will write all configuration to the "traditional" locations and actually have networking functional at boot time.

There is no need to muck around manually editing files using this method.

The Network Manager only configures networking after a login - IMHO it is basically evil and should not be used unless you are doing fancy things like VPN or Wireless.  ;-)

---

