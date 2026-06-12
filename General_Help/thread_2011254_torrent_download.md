---
title: "torrent download"
date: 2012-06-26
forum: General Help
---

### Post by ciscoboy on 2012-06-26
Hello,

I just got a ubuntu version running on my laptop which I use to go online, and one thing I like to do online is to download torrents. Unfortunately, whenever I try to download a magnet torrent, the mozilla firefox thanks hat I'm running tells me that it doesn't recognise the type of webpage, and have therefore been unable to download torrents. Could anyone help me?

Thanks

CiscoBoy

---

### Post by jmfal on 2012-06-26
It could be that the website is IPv6

---

### Post by sanderj on 2012-06-27
> **ciscoboy said:**
> Hello,

I just got a ubuntu version running on my laptop which I use to go online, and one thing I like to do online is to download torrents. Unfortunately, whenever I try to download a magnet torrent, the mozilla firefox thanks hat I'm running tells me that it doesn't recognise the type of webpage, and have therefore been unable to download torrents. Could anyone help me?

Thanks

CiscoBoy

Have you installed a bittorrent client? I would advice 'transmission'.

---

### Post by ciscoboy on 2012-07-01
I am currently using transmission for torrent downloads and is currently working as long as I select direct download. For some reason, magnet downloads will not work for my firefox web browser. And to my knowledge, the most current updates for firefox have been uploaded. 

One last thing; what does IPv6 mean?


Thank You 

CiscoBoy

---

### Post by sanderj on 2012-07-01
> **ciscoboy said:**
> I am currently using transmission for torrent downloads and is currently working as long as I select direct download. For some reason, magnet downloads will not work for my firefox web browser. And to my knowledge, the most current updates for firefox have been uploaded. 

One last thing; what does IPv6 mean?


Thank You 

CiscoBoy

And if you use Chrome? FWIW: magnet links work for me with tranmission (and Chromium).

#IPv6: IPv6 means more IP addresses and no more problems with NAT. If you type "sudo apt-get install miredo" on your Ubuntu, you will (very probably) have working IPv6.

---

### Post by ciscoboy on 2012-07-02
I installed miredo and it looks like it did the trick. I'll let you guys know if I have any other problems relating to this subject.

Thank You

CiscoBoy

---

