---
title: "Network Settings: Can't make locations work"
date: 2006-03-01
forum: General Help
---

### Post by rivasdiaz on 2006-03-01
Hello.

I have a working Ubuntu Breezy installation on my lap, and I have worked with it for around 4 months without any problems. Up to now everywhere I went, I had a DHCP server available, so no problem with only one configuration.
Last monday I started in a new job and for some weird reazons we have static IPs here.
I tried to configure locations in my network settings but I can't make them to work. I have configured "Home" with DHCP and "Work" with my static IP, but it never works, maybe the following problems gives you some ideas.
I then removed both locations and have edited my config network, but when I put the static configuration in the Network Settings, a couple of minutes after applying the changes the network configuration is reset back to DHCP. This happened 3 or 4 times.
Then I checked my /etc/network/interfaces and the configuration is OK (Static IP configured, even if ifconfig eth0 says another IP), with only one minor problem, whenever I edit something from the Network Settings, it adds the line "auto eth0" to my /etc/network/interfaces. I always remove this line because when I don't have a wired network, the booting process takes a lot of time to detect the network problems, and anyway when I plug the wire the network autostarts so I don't need the "auto eth0".
The only way I can get my network working with the static IP is whenever I see that the network is not working, I go to a console and say:
$ sudo ifdown eth0
<I get always an error of some process not found>
$ sudo ifup eth0
<no error, no message here>
<redo the ifdown/ifup process, just to make sure it is working, no errors>
After that my IP is back in static mode. After 4 or 5 tries, it gets fixed in static mode. No more problems until I change config back to DHCP. Changing to DHCP gives me no problems, only changing to static IP.
It seems like some kind of daemon who tries to reconfigure as DHCP in the background.

Could somebody help me finding what's wrong with my network config? And how to make the locations in Network Settings work as expected?

Rivas

---

### Post by schilcha on 2006-03-02
This is actually not a solution to your problem (sorry).
BUT, since I'm in the very same situation (static IP at home, dhpc at work), I can show you my solution, which works really nicely.

I found this solution in the ifupdown documentation at /usr/share/doc/ifupdown/examples/. There is a example-interfaces-file (network-interfaces.gz) that has a setup, in which the laptop tries to determine where you are by pinging one or the other host using the script ping-places.sh (in the same directory). 

The relevant part of my /etc/interfaces looks like this:
```

mapping eth0
        script /etc/network/ping-places.sh
        map 10.0.0.250/24 10.0.0.98 work
        map 10.42.42.250/24 10.42.42.1 home

iface work inet dhcp
iface home inet static
        address 10.42.42.254
        netmask 255.255.255.0
        gateway 10.42.42.1
        broadcast 10.42.42.255
        network 10.42.42.0
        dns-nameservers ip.of.dns1 ip.of.dns2

```
I copied ping-places.sh into the /etc/network/ directory for convenience.

I'm really not sure what to do with the first line ("mapping eth0"). I think it used to be "mapping hotplug", but since I switched to ifplugd it looks the way it is.

HTH!
Good Luck!

---

### Post by rivasdiaz on 2006-03-02
Thanks, I'll check this option to see if I can solve my problem.
It's sad that Network Settings isn't working, I found some bug reports about it.

---

