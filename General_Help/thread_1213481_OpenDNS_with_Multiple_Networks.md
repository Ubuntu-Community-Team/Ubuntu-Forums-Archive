---
title: "OpenDNS with Multiple Networks"
date: 2009-07-14
forum: General Help
---

### Post by shortcut144 on 2009-07-14
So I got this idea and I wanna know if it will work.  If it will, great.  If you know HOW to do it.  Even better.

For those of you who dunno OpenDNS, goto opendns.com and check it out them come back please.

If you do know...

Well I would like to make it so that the configurations I need for OpenDNS happen everytime I connect to a network on my laptop.  Anyone have an idea how to do that?

For extra credit... make it so that I personally cannot change the configuration.  Only a certain user can.

I am quite new to ubuntu so I wouldn't know where to begin.  Any ideas?

---

### Post by Chemical Imbalance on 2009-07-14
Here ya go:

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Just do this (this is what I do):

```


To avoid having your settings get revoked after reboots, or after periods of inactivity you may need to make the following changes via the command line:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ gksudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

```

---

### Post by shortcut144 on 2009-07-14
> **Chemical Imbalance said:**
> Here ya go:

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Just do this (this is what I do):

```


To avoid having your settings get revoked after reboots, or after periods of inactivity you may need to make the following changes via the command line:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ gksudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

```

After reading that last line there, I feel quite silly.  How do I find he name of my network device?

---

### Post by Chemical Imbalance on 2009-07-14
> **shortcut144 said:**
> After reading that last line there, I feel quite silly.  How do I find he name of my network device?

```
ifconfig
```

---

