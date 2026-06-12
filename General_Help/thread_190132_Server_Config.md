---
title: "Server Config"
date: 2006-06-05
forum: General Help
---

### Post by leetcharmer on 2006-06-05
Hello, I've been toying around with the server install CD and I've got an idea for a server that I want to build.  Here's my system specs:

AMD Athlon 2100+
1GB RAM
3 HDDs: 2/80GB IDE; 1/250GB RAID
D-Link DI-624 Router w/ Wireless setup.

Pre-Question:
1) Is it alright to plug my server straight into the router and let it control DHCP? Or should I really invest in a second ethernet card and go Internet -> Server -> Router -> Thin Clients / PCs?
2) I want to keep LTSP in mind so I've formatted the first 80GB HDD as / (and swap) and then second as /home.  I want to turn the 250GB into a storage center -- like a NAS or SAN server; how should I format this and what should it be mounted as?  Can you verify that my formatting scheme is appropriate -- for webservers, I find that sometimes they like to build a partition separate for /var; what are your thoughts?

Alright, here's the plan -- I want to build a server to host my website ([www.crossfirenow.com](www.crossfirenow.com) via LAMP); host my Counter-Strike: Source Server (easy to setup and run); LTSP host for 4 thin clients (home network).  With my current hardware, does this sound doable?  I'm running on a Fiber Optic connection at home (15Mbps down/1.5Mbps up).

First on my list -- webserver:
I've seen some tutorials online with setting up web servers and what-not -- when they speak of domains, they always have server.example.com as their domain, would I change this to server.crossfirenow.com??  Right now, that site is being hosted by 1and1.com -- I would like to experiment with the server I built using that domain name which I have registered through them.  How can I get a DNS setup to switch hosting to my box? :/ I always have problems setting up MySQL after installation, but I'll deal with that later.

Since I know how to do the Counter-Strike server I'll skip that in this post.
Third: LTSP -- could anyone hook me up with resources to get started?

Fourth: Should I have anything else in my server? Ideas?

Thanks for any replies :D!

---

### Post by adamkane on 2006-06-07
You're probably shooting over our heads here.

Please let us know how things go.

I would love to know how you did with a SAN server.

---

### Post by leetcharmer on 2006-06-08
lawl, thanks -- I'll make a tutorial after it's all setup.

---

### Post by Psylon on 2006-06-14
> Is it alright to plug my server straight into the router and let it control DHCP? Or should I really invest in a second ethernet card and go Internet -> Server -> Router -> Thin Clients / PCs?
You will probably want to go with two separate ethernet cards. The ltsp side will need some entries that many stock dhcp servers will be unable to provide. It may be a bit tricky to get your internet side interface to dhcp from the internet and your internal network card to have a static ip address and to provide dhcp services. Turn off dhcp on your "router" or substitute a hub/switch. The newstyle ltsp has an quick install, see [https://wiki.ubuntu.com/UbuntuLTSP/LTSPQuickInstall](https://wiki.ubuntu.com/UbuntuLTSP/LTSPQuickInstall) for more information.

> I want to keep LTSP in mind so I've formatted the first 80GB HDD as / (and swap) and then second as /home. I want to turn the 250GB into a storage center -- like a NAS or SAN server; how should I format this and what should it be mounted as? Can you verify that my formatting scheme is appropriate -- for webservers, I find that sometimes they like to build a partition separate for /var; what are your thoughts?
80 GB is overkill for your system drive. Consider doing something like an 8 GB root, 1 GB swap, 8 GB var or something similiar. I would make your second 80 GB drive a backup drive. Then possibly mount the third drive as /home. My favorite method for backing up small/home servers is a disk-to-disk program called rsnapshot.

Here is how I have my home server layed out:
/dev/hda1             4.7G  2.8G  1.8G  62% /
/dev/hda2             1.0G                  swap
/dev/hda3             4.7G  1.7G  2.9G  37% /var
/dev/hda4             219G   76G  133G  37% /home
/dev/hdb1             116G   95G   21G  83% /backup
/dev/hdc1             233G  197G   37G  85% /mythtv

I would use ext3 for the system drive and xfs for the rest. Of course there is more than 1 way to do it. :-)

Your server should be plenty big enough. Its specs are similiar to mine which serves ut2004 and myth and does a bunch of other stuff including varying diskless clients.

---

### Post by leetcharmer on 2006-06-15
[QUOTE=Psylon]80 GB is overkill for your system drive. Consider doing something like an 8 GB root, 1 GB swap, 8 GB var or something similiar. I would make your second 80 GB drive a backup drive. Then possibly mount the third drive as /home. My favorite method for backing up small/home servers is a disk-to-disk program called rsnapshot.

Here is how I have my home server layed out:
/dev/hda1             4.7G  2.8G  1.8G  62% /
/dev/hda2             1.0G                  swap
/dev/hda3             4.7G  1.7G  2.9G  37% /var
/dev/hda4             219G   76G  133G  37% /home
/dev/hdb1             116G   95G   21G  83% /backup
/dev/hdc1             233G  197G   37G  85% /mythtv

I would use ext3 for the system drive and xfs for the rest. Of course there is more than 1 way to do it. :-)[/QUOTE]

What I ended up doing was:
```
/dev/hda1             73931420    655700  69520128   1% /
/dev/hda5             3.0G                  swap
/dev/hdb1             38464340   1757672  34752764   5% /home
/dev/hdb2             38456340    354632  36148204   1% /var
/dev/sda1            240362656    131260 228021596   1% /public
```

lawl, I guess this is ineffective though.  So, if I go the route of making hda the server, whereas hdb is the backup of hda, -- should swap go on hda still?  or should it be used with my storage drive (sda)?  Also, what is xfs?

---

