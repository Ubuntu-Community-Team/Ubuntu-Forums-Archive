---
title: "Connect network printer to XP VM?"
date: 2012-04-18
forum: General Help
---

### Post by jerome1232 on 2012-04-18
So I am trying setup my HP Officejet 6500 on a WinXP Guest, Ubuntu 11.10 host. I can access the printers configuration page fine from a browser inside the guest but I can't figure out how to add the printer and auto detection doesn't seem to find it.

The printers IP is 192.168.1.71, I can also access it by the name of "HPD736FE" the guest is connected via NAT with an ip of 10.0.2.15, default gateway of 10.0.2.2

I've tried adding it using these addresses

[http://192.168.1.71](http://192.168.1.71)
[http://10.0.2.2/192.168.1.71](http://10.0.2.2/192.168.1.71)
[http://HPD736FE](http://HPD736FE)

Any idea's on how to add it would be great, I'm sure it's possible since I can access it's configuration page.

edit: and yes I am putting off my precalc homework why? :P

---

### Post by JKyleOKC on 2012-04-18
For a network connection between two devices to succeed, they must both be on the same subnet. Your printer is on the 192.168.1.0 subnet while the VM is on the 10.0.0.0 subnet.

You can go into the XP Control Panel's Network applet, and change the TCP/IP address from 10.0.2.15 to 192.168.1.xxx where xxx is any number less than 254 that is not already in use on other network devices. This should fix things, if your other network devices are on the 192.168.1.xxx subnet.

However if your other devices are on the 10.0.2.0 subnet, then you'll have to change the IP address of the printer to put it on the same subnet. You'll have to check the printer documentation to find out how to change its IP address. Its gateway would also have to be changed to be the same as that on your XP VM.

I have a very old HP network-printing adapter and it came with a CD that includes (Windows) software for configuring the IP addresses; your printer is probably different but should include the same information somewhere.

Hope this helps!

---

### Post by uidb4056 on 2012-04-18
If you don't need to have NAT on your guest you can try to change NAT to Bridge then you will have all in the same subnet.

---

### Post by jerome1232 on 2012-04-18
> **JKyleOKC said:**
> For a network connection between two devices to succeed, they must both be on the same subnet. Your printer is on the 192.168.1.0 subnet while the VM is on the 10.0.0.0 subnet.


You know that was my first assumption, but upon getting the printers web based configuration despite the separate subnets (I assume the host acts as a gateway between the 2 networks?), I thought adding the printer would work as well.

Well I tried bridged mode, now it's in the same subnet. Still no luck, I'm downloading hp's whooping 300mb driver download right now. I'll post back soon.

And people say windows is easy :lolflag: (had to fit a snarky comment in)

---

### Post by jerome1232 on 2012-04-18
Bridged mode and the HP driver waved it's magic fingers and got it working! I don't know why I didn't think about downloading the driver.

Thanks!

---

