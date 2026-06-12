---
title: "Bus Error/ stack dump"
date: 2011-03-22
forum: General Help
---

### Post by sandman88 on 2011-03-22
I am running ubuntu 10.04 server edition, in it I am running 4 separate hard drives combined into 1 virtual drive, if you look at the paste below, you can see I am not out of disk space, but am getting a bus error, any Ideas what I managed to break?



  System information as of Tue Mar 22 01:21:22 MDT 2011

  System load:    0.0               Memory usage: 13%   Processes:       112
  Usage of /home: 60.8% of 3.61TB   Swap usage:   0%    Users logged in: 0

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

*** System restart required ***
Last login: Fri Mar 18 17:25:45 2011 from 192.168.1.112
sandman@ninjaserver:~$ rtorrent
Caught Bus error, dumping stack:
Stack dump not enabled.
A bus error probably means you ran out of diskspace.
Aborted





update:

so after looking online better, I discovered that an issue such as this can occur if rtorrent stops via a system wide shut down instead of just stopping rtorrent first. I deleted the files and I am running them through rtorrent again, seems to be working fine now.

---

