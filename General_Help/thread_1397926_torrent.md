---
title: "torrent"
date: 2010-02-03
forum: General Help
---

### Post by arunkmohan18 on 2010-02-03
hi
i am using transmission bittorrent client in ubuntu to download files but when i continue same file in windows (bittorrent) it shows error please any one help me for this
is there bittorrent that can use in ubuntu also

---

### Post by lovinglinux on 2010-02-03
Do you have the permissions to save the file from Windows? Looks like Transmission is having permission problems.

I would recommend Deluge and KTorrent. Best torrent clients IMO.

---

### Post by hemimaniac on 2010-02-03
Well first things first, are the torrents being downloaded to a folder that both windows and ubuntu can see (ie. a folder in a ntfs or fat32 partition like another HDD)? Do both OSes have write read permissions to that folder?

using a client in each OS should only muck about with the actual torrent data (record of process) I can use rtorrent in *unix and utorrent in windows, only problem is occasionally the .torrent may have to be rechecked

---

### Post by Bradj47 on 2010-02-03
> **lovinglinux said:**
> 
I would recommend Deluge and KTorrent. Best torrent clients IMO.

Agreed.

---

### Post by arunkmohan18 on 2010-02-04
transmission bittorrent client at starting time it downloading correctly but after an hour it slow down and when i trying to close it shows not responding why this is happenning

---

### Post by arunkmohan18 on 2010-02-04
when i open properties of tha filesystem it shows permissio could not be determined

---

### Post by kantu on 2010-02-04
Speed of torrents cannot be constant or predictable ... Try other torrent clients as mentioned .. and yeah i think qBit torrent is also good

---

### Post by arunkmohan18 on 2010-02-06
i tried deluge but it also downloading in 30kbps but in windows using bittorrent is ok it giving 170kbps

---

### Post by kantu on 2010-02-06
You should monitor uploading also some torrents will be uploading more,then you wont get enough bandwidht fot downloading

---

### Post by lovinglinux on 2010-02-06
> **arunkmohan18 said:**
> i tried deluge but it also downloading in 30kbps but in windows using bittorrent is ok it giving 170kbps

[BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

