---
title: "How to partition and software RAID in Ubuntu 11 Desktop? Newbie help please."
date: 2012-02-08
forum: General Help
---

### Post by MaherLtd on 2012-02-08
Hi,
I am new to Linux and Ubuntu and have read a few sites to get an idea of what partitions are in Linux, etc.
I also found a good site that explains how to do what I am asking but for an older version of Ubuntu [http://www.dedoimedo.com/computers/linux-raid.html](http://www.dedoimedo.com/computers/linux-raid.html)
 
Could someone please point me to a relevant tutorial for Ubuntu 11 Desktop or just let me know what bits I change when installing as I dont see the RAID screen in the desktop version. I installed the server and it was similar to the tutorial I have listed and I did manage to create a software RAID drive.
 
My HP Microserver has 2 TB drives which want to be RAID 1 with 1TB allocated for a time machine backup and 1TB allocated for films, documents, music etc. 
 
I am going to then instal airvideo to allow me to connect my iPad and stream films.
 
If anyone can help with this I would greatly appreciate it.
 
Cheers

---

### Post by jerrrys on 2012-02-09
A bit dated, but Dedoimedo is an excellent site for gparted.  If you need more reference material:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+RAID+1&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+RAID+1&sa=Search&cof=FORID:9)

---

### Post by SaturnusDJ on 2012-02-09
If you want to do what the do here: [http://www.dedoimedo.com/computers/linux-raid.html#mozTocId464958](http://www.dedoimedo.com/computers/linux-raid.html#mozTocId464958)
Get the alternate installer from over here: [http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)
(Tutorial also says this. :) )

If you already have an OS installed, you must use mdadm commands, or if the newer Ubuntu versions still contain Disk Utility (in the System menu) that is in 10.04 you can use that tool to create arrays. File --> Create --> RAID Array.

---

