---
title: "Transfer tons of files between two laptops on my desk"
date: 2012-06-29
forum: General Help
---

### Post by tomkat3 on 2012-06-29
Hello everybody,

I just got a new laptop with a very nice 500GB hard drive that is replacing an older laptop with a 120GB hard drive and a xubuntu/windows vista dual boot.

What I'd like to do now is to transfer around 30GBs of files (music and other smaller files) to the newer machine (windows 7 and xubuntu). I was about to start moving everything over with a 8GB USB memory stick, but that seems a little silly. Is there a more 'set it and forget it' way?

I was hoping at first to hook the two laptops together with an ethernet cord and move things through there. Google told me that samba or ssh would be the simplest way to do it, but fumbling around with those hasn't really gotten anywhere. :| What is the easiest way to do what I want?

---

### Post by GreatDanton on 2012-06-29
If you don't mind spending a couple of bucks for external drive this will be the best option. You transfer the files and also have the backup.

If you wanted to do this as fast as possible then transfer with USB. I think that will be much faster than setting up samba (if you are not familiar with).

Hope this helps.

---

### Post by matt_symes on 2012-06-29
Hi

If you can connect them both to a network (maybe to the same wireless access point or both through a wired hub) then i would use rsync to do the job for you.

Kind regards

---

### Post by Mopar1973Man on 2012-06-29
Matt's right if you got a good solid wired network you could use 1 GBit connect and really transfer stuff fast compared to any USB external drive which would be slower.

If you have to you could make a network cable for laptop to laptop without using the router... ;)

---

### Post by tomkat3 on 2012-06-30
rsync seems to be exactly what I want! So I'd connect both laptops to the wireless router? I can't simply put a ethernet cable between the two?

I could probably do all this in 30 minutes or so with my USB stick, but I'd like to learn how to use more elegant tools for future prosperity! :KS

---

### Post by wheeze on 2012-06-30
> **tomkat3 said:**
> I can't simply put a ethernet cable between the two?

You can but the cable has to be a crossover cable, it can't be a standard cable. The connections to one of the pins in the plug is reversed in a crossover cable. If your wireless router has ethernet ports on it you can plug both machines into the router with standard cables.

---

### Post by speedwlk on 2012-06-30
Using the network cable, you can try out the following:
[see [https://help.ubuntu.com/community/Internet/ConnectionSharing/]](https://help.ubuntu.com/community/Internet/ConnectionSharing/])


Steps:
1> Connect one end of the network cable to your old laptop and the other end to the new one.
2> In your old laptop, the connection might show up with "Auto eth0". Choose to "Edit connections" under network manager; go to IPv4 setting -> method : set it as "Shared to other computer". Save the setting and refresh the connection.
3>your new laptop should now be connected through the wired connection. If not, just disconnect and then reconnect the wired connection from the network manager.
4> Your old laptop will have ip 10.42.0.1 and the new one 10.42.0.xy; 


Now you can use ssh to transfer files if you like. Otherwise, move files [to be copied from the old laptop] to the Public directory under home and then access the files over the network from the new laptop.


Hope it helps.

---

### Post by holycow131415 on 2012-06-30
You could buy a network storage drive ;)

---

### Post by Morbius1 on 2012-06-30
TransferOnLan: [http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)

It's a java jar file so it will work on anything ( Windows, Linux, OSX .. ) that has java installed on it. You don't install it or configure it you just extract it and run it.

---

### Post by GreatDanton on 2012-06-30
> **speedwlk said:**
> Using the network cable, you can try out the following:
[see [https://help.ubuntu.com/community/Internet/ConnectionSharing/]](https://help.ubuntu.com/community/Internet/ConnectionSharing/])


Steps:
1> Connect one end of the network cable to your old laptop and the other end to the new one.
2> In your old laptop, the connection might show up with "Auto eth0". Choose to "Edit connections" under network manager; go to IPv4 setting -> method : set it as "Shared to other computer". Save the setting and refresh the connection.
3>your new laptop should now be connected through the wired connection. If not, just disconnect and then reconnect the wired connection from the network manager.
4> Your old laptop will have ip 10.42.0.1 and the new one 10.42.0.xy; 


Now you can use ssh to transfer files if you like. Otherwise, move files [to be copied from the old laptop] to the Public directory under home and then access the files over the network from the new laptop.


Hope it helps.


+1. That's the best solution. Since you mentioned Windows machine, if it's possible to connect both computer to the same router, then you can create shared files and then just copy your files via LAN.

---

### Post by rhianlopez on 2012-07-31
you can transfer the files by conencting the devices in a network. Connect the devices in a network through a cable or wireless network after which share the files of the other device or just share a drive in the other device (network sharing) so that you can copy to the other's drive files from your computer, be sure to turn on network discovery so that each computer will detect the other, check aslo this help for other steps  [http://www.techyv.com/questions/how-share-file-network]("http://www.techyv.com/questions/how-share-file-network")

---

