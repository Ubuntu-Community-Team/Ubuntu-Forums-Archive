---
title: "Cant seed/leech personal torrent"
date: 2011-02-07
forum: General Help
---

### Post by groosam on 2011-02-07
Hey everyone
I'm having quite some trouble with trying to seed/leech a torrent I've created.  

I'm starting with some small text files to get the system working before moving on to transfer some big video files.  From the instructions I've gotten from the web all I need to do is select the file, its destination folder, and choose to select the private box and maybe add some trackers.  I'm using Transmission.   

The .torrent files are loading just fine.  I've tried not using a tracker on one private torrent (nothings transferring), a tracker on another private torrent, and no tracker on another, without selecting the private box.

I'm using [http://tracker.openbittorrent.com:80/announce](http://tracker.openbittorrent.com:80/announce) as the tracker.  So far all it says under the torrents information is 'Peer list request timed out 13 minutes ago; will retry
 Asking for more peers in 18 minutes
 Got a scrape error "tracker did not respond" 14 minutes ago
 Asking for peer counts in 18 minutes'

[http://openbittorrent.com/](http://openbittorrent.com/) offers the public tracker
The simple instructions are to add the link to the tracker list of the torrent.. except Transmission doesn't accept 'udt://tracker.openbittorrent.com:80/announce'.  I've seen on the web changing the 'udt' to 'http' would work. 

Might that be where my problems lie?  
Why does Transmission not like the 'udt'?

A source on a website made it seem like as long as the .torrent files are the same files on both ends you don't need to include a tracker if its a personal torrent and as long as the seeding computer doesn't shut off.

Any suggestions?...

---

### Post by groosam on 2011-02-07
bump

---

### Post by groosam on 2011-02-07
The file loads on Deluge as the seeding machine, with udp://tracker.openbittorrent.com:80/announce working as the tracker.
When I try leeching from Transmission no tracker appears in the properties menu of the torrent.  When trying to enter udp://tracker.openbittorrent.com:80/announce as the tracker it says 'list contains invalid urls'.

??

---

### Post by groosam on 2011-02-07
Any input? 
Does anyone know if openbittorrent's tracker is working presently? 
Any suggestions of other trackers; or if one isn't needed, any steps to setting up a private torrent for one to several computers?

---

### Post by kem on 2011-08-15
I confirm it. Very same issue here.

---

### Post by jayboe on 2012-04-23
Transmission and ktorrent both will download just fine, but wont upload for me either. Been beating my head up against the wall with with firewall settings to no avail. I even uninstalled ufw and ran iptables -F and iptables -X and ran iptables -L and got this

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

So everything should be honkey-dorey but its not. Im new to the firewall stuff but I know that ufw is just a frontend for iptables and its easier to use so I have tried a few ufw commands to open a port but when I test it from transmission it sais that the port is closed.
ufw allow [someport]/tcp
ufw allow [someport]/udp
ufw allow [someport]

I am all googled out on this topic and time is of the essence. I am about to abondon precise and go back to lucid. Desperately seeking help,
                                                                               jayboe and many others :popcorn:

p.s. this isn't specific to my personal files either. even if I download another file it goes fine until the download finishes. In Ktorrent I see that it is trying to upload but acts like something is kicking in and holding it back.

---

### Post by EduardoMartins on 2013-01-09
Has anyone found a solution for this problem?

---

