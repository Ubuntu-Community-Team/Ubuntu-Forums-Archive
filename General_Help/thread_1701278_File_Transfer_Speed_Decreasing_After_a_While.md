---
title: "File Transfer Speed Decreasing After a While"
date: 2011-03-06
forum: General Help
---

### Post by Morientes on 2011-03-06
Anyone know what might cause a file transfer to start out fast (11-12 mb/sec) and then drop to about 1 mb/sec after having downloaded about 2 gb?
This is what happens when I download files from my old fit-pc 1.0 (a small mini PC with 256 MB/RAM, an AMD Geode processor, and a 100 mbps network card) via ftp over my local network.
Is it some buffer filling up? I was directed to some article about "bufferbloat" earlier ([http://gettys.wordpress.com/2010/12/03/introducing-the-criminal-mastermind-bufferbloat/](http://gettys.wordpress.com/2010/12/03/introducing-the-criminal-mastermind-bufferbloat/)), but I did not get any solution from that unfortunately. I have tried increasing the server's TCP buffer using these instructions: [http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu](http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu) , but it does not make any difference. Any ideas?

By the way, I am running Ubuntu Server 10.10 on the fit-pc and Ubuntu 10.10 desktop on the connecting client (which is just a normal Core 2 duo, 4 gb ram computer).

UPDATE: I should add that things were working fine when I was using ubuntu 7.10, but are not now that I have installed 10.10...

UPDATE 2: I just found out this is ONLY a propblem when transferring files to ubuntu. If I use winscp from Windows 7, the transfer speeds are fine...

UPDATE 3: problem solved! It seemed it was gFTP that was the culprit. Transferring the files using filezilla instead in Ubuntu yields an excellent rate of 11.8 MB/sec. Anyone have an idea what might be wrong with gFTP?

---

### Post by JRV on 2011-03-06
Could it be this problem?

Run "top" from the command line.

If "gvfsd-metadata" is hogging your processor do this:

```

rm -rf /home/USERNAME/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

---

