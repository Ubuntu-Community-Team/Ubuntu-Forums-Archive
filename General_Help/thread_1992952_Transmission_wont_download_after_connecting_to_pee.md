---
title: "Transmission wont download after connecting to peers"
date: 2012-06-01
forum: General Help
---

### Post by celebratinglife on 2012-06-01
Ubuntu 12.04 :My transmission is not downloading anything even after connecting to more than 60 seeders. If the same torrent is used in deluge, the download starts instantly! 
Everything was working well in 10.04. But after a fresh install of 12.04, transmission and google chrome doesnt work but deluge, mozilla and opera are working nicely!
I can adjust for chrome but I want to use transmission not deluge.
Help plz.

---

### Post by celebratinglife on 2012-06-02
Somebody plz respond! Plz!

---

### Post by mutap on 2012-06-02
Did you try to set up high torrent priority?
Click properties on torrent, than options and set high priority.
That helps me to start downloading immediately.
I didn't use Transmission before, so I can't help you more, but when priority is normal, there is no download, when it's high, it works fine(in my case). :)

---

### Post by celebratinglife on 2012-06-04
> **mutap said:**
> Did you try to set up high torrent priority?
Click properties on torrent, than options and set high priority.
That helps me to start downloading immediately.
I didn't use Transmission before, so I can't help you more, but when priority is normal, there is no download, when it's high, it works fine(in my case). :)

setting the priority high didnt help! More suggestions plz!

---

### Post by sid32 on 2012-06-21
I'm having the same issue in 12.04. Torrents from different tracks just sit there. Deluge works just fine, same torrents and I hit my top speed in seconds. Think it has something to do with my upgrade of libgtk-3-0 files to 3.4.2-0ubuntu0.3 from the testing repos.

---

### Post by celebratinglife on 2012-06-22
> **sid32 said:**
> I'm having the same issue in 12.04. Torrents from different tracks just sit there. Deluge works just fine, same torrents and I hit my top speed in seconds. Think it has something to do with my upgrade of libgtk-3-0 files to 3.4.2-0ubuntu0.3 from the testing repos.

I dont know about libgtk updates but I keep my machine updated by all the updates provided by official repos. Any solution????

---

### Post by VCoolio on 2012-06-22
Check properties > options > maximum peers for the new torrents. I remember some problem with default max peers being set to 0. Then it won't download. Just a thought, may not be your issue.

---

### Post by reefis on 2012-09-04
I'm having the same issue. Has anyone figured it out or should I just get Deluge... why bother

---

