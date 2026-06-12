---
title: "Hey does any of you tech experts know how to set this up?"
date: 2010-07-28
forum: General Help
---

### Post by Legendary_Bibo on 2010-07-28
Well the new semester is starting up, so me and my brother decided that we should make our own file server for media, and school work so we're thinking about getting [two 2 TB hard drives](http://www.amazon.com/Western-Digital-Intellipower-Desktop-WD20EARS/dp/B002ZCXK0I/ref=sr_1_1?ie=UTF8&s=electronics&qid=1280375453&sr=8-1), and a two bay storage array that would support 4 TB. For now we just need to know the hardware that would work. Although we were wondering something. Does it need to be connected to a computer at all? Or do we just have to plug in an ethernet cable? Also how would we set it up to let people access it from anywhere? I know we'll have to set it up as NTFS probably because my bro uses Windows, and Linux can read NTFS.

---

### Post by Dustin2128 on 2010-07-29
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)
google is your friend ;)
As for what distro to use, I'd recommend debian because of stability.

---

### Post by mkendall on 2010-07-29
> **Dustin2128 said:**
> I'd recommend debian because of stability.

Stability on a server? Bah! Where's the adventure in that?

---

### Post by jerenept on 2010-07-29
NTFS is totally unnecessary, if it being shared over Ethernet to other computers.

In answer to your question, there are networked HDD systems called NAS or Network Acessed Storage, and NAS units do not require a computer, but the bare Harddrives you have there require a computer to work.

This computer can be set up with [FreeNAS]("http://sourceforge.net/projects/freenas/files/stable/") ( a good review [here]("http://www.smallnetbuilder.com/content/view/30179/75/").)

---

### Post by dcollier on 2010-07-29
I would have to agree, FreeNas is the way to go.  And easy to set up.  Available to any one one your network and you can even setup permissions.  It even has a torrent application.  FreeNas is the way to go.

---

### Post by drdos2006 on 2010-07-29
+1 for FreeNAS

regards

---

### Post by cariboo on 2010-07-29
+1 for Freenas, you can run it from a flash drive.

---

### Post by Legendary_Bibo on 2010-07-29
> **jerenept said:**
> NTFS is totally unnecessary, if it being shared over Ethernet to other computers.

In answer to your question, there are networked HDD systems called NAS or Network Acessed Storage, and NAS units do not require a computer, but the bare Harddrives you have there require a computer to work.

This computer can be set up with [FreeNAS]("http://sourceforge.net/projects/freenas/files/stable/") ( a good review [here]("http://www.smallnetbuilder.com/content/view/30179/75/").)

Okay cool, I think that's what were looking at. We were looking at [these kind of things](http://www.amazon.com/Western-Digital-ShareSpace-Ethernet-Attached/dp/B001FAE64K/ref=sr_1_3?s=electronics&ie=UTF8&qid=1280375551&sr=1-3)

Is this what you're referring to? Also, we don't know the first thing about setting up a server, so hopefully this is easy. We want to set it up where we just have to keep it plugged in, and have something where we access it from anywhere with an internet connection to only people with permissions (i.e. me, my brother, a few of our friends, our dad) to read and write stuff to it. Is it easy to set up with FreeNAS, and do we have to have a NAS plugged into a computer, it'd be fine if we did, I have an old Dell already hooked up with Lubuntu if that'll work?

---

### Post by v1ad on 2010-07-29
im pretty sure if you want to access the nas you would have to go through another computer. unless it is remote accessible. all depends on the nas.

---

### Post by aeiah on 2010-07-29
if you aren't providing it yourselves and are just adding hdds to a two-bay NAS like the one you linked, then you don't really have to think too hard about the setup. it'll act as an autonomous filesever. it'll probably run on an embedded linux and offer samba, ftp and nfs. if you're allowing access by the outside world then hopefully it'll allow sftp (ssh) too. you'd just forward the port on your router for incoming port 22 traffic (for ssh/sftp)

you might want to consider getting one that can run a bittorrent client too, that way you can download all your legally obtained linux distros without having your computer turned on.

a lot also provide daap and upnp, so you can stream your media over the lan.

they usually have fairly easy to use web control panels for administration, so there isnt too much that can go wrong. just make sure you know what you're doing if you open it to the outside world.

---

### Post by Paqman on 2010-07-29
> **Legendary_Bibo said:**
> do we have to have a NAS plugged into a computer

NAS stands for Network Attached Storage. You just connect it up to your network and then you can access it from any machine on that network. Depending on the model of NAS you might also be able to set it up for access from outside of your network.

+1 for getting one with a torrent client. Running an ARM-powered NAS overnight to download torents is much more efficient than running a whole PC.

I'd also recommend using some level of redundancy if you're putting all your data on it. RAID1 is the minimum level of protection.

---

### Post by overdrank on 2010-07-29
Moved to General Help

---

### Post by cascade9 on 2010-07-29
> **Legendary_Bibo said:**
> Well the new semester is starting up, so me and my brother decided that we should make our own file server for media, and school work so we're thinking about getting [two 2 TB hard drives]("http://www.amazon.com/Western-Digital-Intellipower-Desktop-WD20EARS/dp/B002ZCXK0I/ref=sr_1_1?ie=UTF8&s=electronics&qid=1280375453&sr=8-1"), and a two bay storage array that would support 4 TB. 

Unless you really like partitioning from command line, avoid those WD 'EARS' drvies. They use 4k sectors, not the standard 512B sectors, but they report to the OS as 512B sectors. PITA to setup with linux.

> **Paqman said:**
> I'd also recommend using some level of redundancy if you're putting all your data on it. RAID1 is the minimum level of protection.

Probably not a bad idea, but that would make 2x2TB drives 2TB, not the 4TB that Legendary_Bibo wanted. 

Maybe 3x2TB RAID 5 would be a better idea than 2x2TB JBOD (just bunch one disc) or worse yet, 2x2TB RAID 0. That way there is still 4TB, but some data protection.

---

### Post by Paqman on 2010-07-29
> **cascade9 said:**
> 
Maybe 3x2TB RAID 5 would be a better idea than 2x2TB JBOD (just bunch one disc) or worse yet, 2x2TB RAID 0. That way there is still 4TB, but some data protection.

Absolutely, although you do step up quite a bit in price to get a box capable of RAID5, plus the cost of your extra drive(s). If price was an issue you could always get a RAID5 capable machine and run it as RAID1. Then if you ran out of storage you only need to buy one more drive to expand to RAID5, and in the meantime you've got the redundancy.

---

### Post by Legendary_Bibo on 2010-07-29
> **Paqman said:**
> Absolutely, although you do step up quite a bit in price to get a box capable of RAID5, plus the cost of your extra drive(s). If price was an issue you could always get a RAID5 capable machine and run it as RAID1. Then if you ran out of storage you only need to buy one more drive to expand to RAID5, and in the meantime you've got the redundancy.

You've lost me. I have a faint of an idea of what RAID is, it's where you have multiple hard drives, and your system can treat both as one hard drive, but it increases the speed dramatically. Welp, we already knew that we were going to have to learn this stuff to set up. I'm sure we won't need that much protection because we plan on only letting some people have access to it, and I can't believe I forgot the Upnp, we'll have to look at that. Would we have to set up torrents in order to do file transfer? Man, there's going to be a lot to learn, but it'll be nice to have our own little server. :D

So is there a way like an application that would give someone a connection to our server from anywhere and treat it like it's a normal folder on the computer?

I'll definitely be coming back with more questions when we get it.

---

### Post by endotherm on 2010-07-29
> **Legendary_Bibo said:**
> Well the new semester is starting up, so me and my brother decided that we should make our own file server for media, and school work so we're thinking about getting [two 2 TB hard drives]("http://www.amazon.com/Western-Digital-Intellipower-Desktop-WD20EARS/dp/B002ZCXK0I/ref=sr_1_1?ie=UTF8&s=electronics&qid=1280375453&sr=8-1"), and a two bay storage array that would support 4 TB. For now we just need to know the hardware that would work. Although we were wondering something. Does it need to be connected to a computer at all? Or do we just have to plug in an ethernet cable? Also how would we set it up to let people access it from anywhere? I know we'll have to set it up as NTFS probably because my bro uses Windows, and Linux can read NTFS.
i have a NAS, which is essentially an external enclosure with a network port (and an embedded linux os). I love it. far faster and more reliable than my server box.

---

### Post by dcollier on 2010-07-29
You don't have to set up raid from the start, "this is just one of the powerful features of FreeNas".  Oh and it also has upnp functions.

---

### Post by Paqman on 2010-07-29
> **Legendary_Bibo said:**
> You've lost me. I have a faint of an idea of what RAID is, it's where you have multiple hard drives

That's the one.

> and your system can treat both as one hard drive, but it increases the speed dramatically.

It either increases the speed, gives you redundancy, or both. There's lots of different kinds of RAID. In a redundant array, disks mirror each other's contents. When one fails (it's a hard drive, after all) you don't lose any data. You just swap the faulty disk for a new one.

> 
So is there a way like an application that would give someone a connection to our server from anywhere and treat it like it's a normal folder on the computer?


You can mount a network share as a local folder, yes. To do so you connect to it using a network protocol such as NFS or SMB/CIFS. Generally this means adding a single line entry to /etc/fstab. You can use a GUI like mountmanager to do this for you.

---

### Post by cascade9 on 2010-07-30
> **Legendary_Bibo said:**
> You've lost me. I have a faint of an idea of what RAID is, it's where you have multiple hard drives, and your system can treat both as one hard drive, but it increases the speed dramatically. 

It can increase speed...or it can slow you down (RAID 0). 

Not that speed is an issue over a network, even with gigabit you are limited to 125MB/sec (theoritical), with 100MB/sec being as much as you should really hope for.....and a single HDD can crack 100MB/sec these days.

---

