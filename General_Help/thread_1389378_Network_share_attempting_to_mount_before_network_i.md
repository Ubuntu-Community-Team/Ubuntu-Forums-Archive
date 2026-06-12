---
title: "Network share attempting to mount before network is up"
date: 2010-01-24
forum: General Help
---

### Post by daniel.pool on 2010-01-24
Hi all,

I have a Karmic server install on which I've set up a network drive mapping to a NAS (CIFS). I'm having trouble with automounting the disk though, as (from what I can tell) the disk is attempting to mount before the network is up.

dmesg shows the following:
```

[   10.421192] lirc_dev: lirc_register_driver: sample_rate: 0
[   10.427116] lirc_mceusb[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb4:2
[   10.427223] usbcore: registered new interface driver lirc_mceusb
[   11.663291] usplash:309 freeing invalid memtype fffffffff7000000-fffffffff7e00000
[   16.062579]  CIFS VFS: Error connecting to socket. Aborting operation
[   16.062597]  CIFS VFS: cifs_mount failed w/return code = -113
[   26.248817] r8169: eth0: link up
[   26.250337] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.790026] eth0: no IPv6 routers present

```I've tried looking for some way of changing the start up order of services, but the only information I've been able to find is how to turn the start up services on or off using a gui. Can someone point me in the right direction for sorting this?

Cheers,
~Dan

p.s. Sorry, I should mention that executing mount -a after the system (and network) has started will successfully mount the disk.

---

### Post by nimrodwebdesign on 2010-02-25
I had the same thing, and eventually found the answer. I just had to add the following option, in [FONT="Courier New"]/etc/fstab[/FONT], for that mount:


[INDENT][FONT="Courier New"]**_netdev**[/FONT][/INDENT]


That says the mount is on a **net**work **dev**ice, and that it therefore needs to wait for the network.

It turns out this is actually in the man page for mount. Doh, I should have FTFM'd. ;)

Anyway, I hope that helps,
Colin :)

---

### Post by daniel.pool on 2010-03-07
Hey Colin,

Thanks for the response ... missed it amongst a pile of unread email (I'm being pretty disorganised right now). Much appreciated though.

When I get a moment free I'll try that out to see if it helps,
Cheers
~Dan

---

### Post by ionplay on 2012-03-30
cifs_mount failed w/return code = -113

I have that same error
but it just happens after my network dies

Ubuntu 8.0.4 with r8168 driver

did you two ever resolve anything here????

---

