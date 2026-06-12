---
title: "Server: Where to use the faster hard-drives"
date: 2010-05-02
forum: General Help
---

### Post by iMisspell on 2010-05-02
Going to be setting up a local home server ("headless") for the following:
* General file sharing for home network
 -- a portion of this will be for movies which are accessed via Popcorn-Hour and a second PC hooked to another TV
* MySQL storage for home network (bills, misc info, bookmarks, code snippets, etc.)
* PHP Server for php scripts i write
* SVN
* misc Databases for PHP dBase testing (SQLite and Postgre) 
* Virtualbox
* backing up stuff

I have a bunch of hard-drives of different sizes, buffer size and access speeds.

Hardware
* m/b _[supermicro X7SBL-LN2]("http://www.supermicro.com/products/motherboard/Xeon3000/3200/X7SBL-LN2.cfm")_
* Intel Xeon X3360 Yorkfield 2.83GHz 12MB L2 Cache LGA 775 95W Quad-Core Processor
* (2) (8GB in total) Crucial 4GB (2 x 2GB) 240-Pin DDR2 SDRAM ECC Unbuffered DDR2 667 (PC2 5300) Dual Channel Kit Server Memory Model CT2KIT25672AA667
* (known hdd) Western Digital Caviar Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

What would be the best way to set this up ?
OS installed on fast hdd ?
Virtualbox on fast hdd ?
Movie storage on fast hdd's (mirror raided) ?

As for raid, i plan on taking two (1TB) hdd's and mirror them for the movies and two more (smaller) mirrored for backup storage.

Im pretty sure i would want the Movies stored on there own hard-drive (faster hdd with more buffer) so not to cause and "lag" incase the server is being used/access at the same time for another use (MySQL access or what ever).

Currently the server machine is set-up using VMware which is where the current Ubuntu-server is installed to/on, but now i would like to have Ubuntu as the base and use Virtualbox as means to virtual hosting instead of VMware.

Thanks for any guidance.

_

---

### Post by Steven_S on 2010-05-02
In my opinion... if you are going to use a router in your network, the speed of transmission of data will probably always be limited by that, rather than by the speed of your HDD. 

I stream movies myself (directly from my home-built "server" to my tv, through a home network). The machine is a dual-core (a recycled pentium 4, 3 Ghz). I have not had any problems, even with only a 100mbps network card in the server and a 54 mbps router in-between. If I remember it right, a 90-minute 13GB movie would need a transfer speed of 20 mbps (which would be around 2,5 MB per second). A HDD transfers at about 70 MB per second (source: [http://en.wikipedia.org/wiki/Hard_disk_drive#Data_transfer_rate](http://en.wikipedia.org/wiki/Hard_disk_drive#Data_transfer_rate)), so I wouldn't worry too much about that. 

In other words: if you are going to have a strategy on this: for streaming, you don't seem to need the newest and the fastest...

---

### Post by Jive Turkey on 2010-05-02
I disagree with steven_s.  If you have gigabit LAN your bottleneck will often be the disk write speeds.  You will only hit this on large file writes over the LAN though.  The slower HDDs should be able to serve the movies just fine but writing the movies to them would be slower.  I'd recommend using the faster HDDs for the OS, your development/database stuff as that is where you are likely to see a difference.  I've read that ext3 is faster in most cases too.

---

### Post by iMisspell on 2010-05-02
Thanks for the feed back...

While looking at some of the drives here, theres a few which are IDE, which the m/b does not support. So while looking for a controller, came across a *Western Digital Caviar Green WD5000AADS 500GB 32MB Cache SATA 3.0Gb/s 3.5"* for $55. I think im gonna grab two of them, mirror raided and then install the O/S on there along with the main MySQL storage.

Use the older IDE's mirrored, for the backup storeage and then raid the other SATA's for the movies and files storage.

Still would love to here other peoples opinions on how they would set this up.

[edit]
Note:
Have a Netgear GS108 Switch - PROSAFE® 8-PORT GIGABIT ETHERNET DESKTOP SWITCH 10/100/1000 MBPS

_

---

