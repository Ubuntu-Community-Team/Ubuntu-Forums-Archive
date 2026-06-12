---
title: "Torrent, even inactive, eats up all bandswidth."
date: 2010-06-19
forum: General Help
---

### Post by Barafu Albino Cheetah on 2010-06-19
I use Transmission 1.03(tried prior versions too) for BitTorrent. When application is on, and uploading even at 1 kbs rate, all my 10000 kbs(real) traffic seems blocked. Web pages are being opened for several minutes, and frequenty timeout. 
When bittorrent is on, and not uploading anything, even when downloading, there is no problem. 
No problem in other OSes, or KTorrent. Need exactly Transmission, though.

---

### Post by inso_741 on 2010-06-19
try deluge

---

### Post by s.v.z on 2010-06-19
This happens because torrent clients keep a lot of half-open connections, which take a lot of router cpu time to be processed. Also some providers allow a limited number of connections. Probably your upload banwidth is smaller. Try reducing connection count in your torrent-client`s config.

---

### Post by NFblaze on 2010-06-19
Do you use Comcast?

If you do Comcast is notorious for this bull. I've had this done to me in two different locations, by Comcast though to be fare I probrably was up/downing quite a bit of data before they started doing it.

I never found a way around it except, in the first location I lived I would just say screw them and keep the torrent program running for much longer, eventually they stopped throttling me. Where I live now, is relatively new throttling (I guess they saw my data usage over a couple of months), I usually just reset my modem for like 4minutes.

---

### Post by Linuxforall on 2010-06-19
Tranmission has been updated to latest version 2.00, in Lucid you should have version 1.93 which works quite well. To update to latest Transmission, add their PPA by pasting sudo add-apt-repository ppa:transmissionbt/ppa 

Then do sudo apt-get update and go to update manager to click on all updates showing.

---

### Post by Barafu Albino Cheetah on 2010-06-20
Updated to 2.00. Now it behaves better, though still other programms are too slow. However, you an tolerate it now.

---

