---
title: "Adding Torrents to Deluge I've Already Downloaded"
date: 2011-02-05
forum: General Help
---

### Post by Eggness on 2011-02-05
I just got all my files from my old computer onto the one I'm  currently using.  I'm trying to get all my torrents onto Deluge so I can  start seeding again, but I'm having some trouble.  I've moved all the  files into a directory and told Deluge to use that directory as the  location where torrents are downloaded to, but when I start up the  torrents they start re-downloading.  

How can I get Deluge to detect that I have the files on my computer already?  The Deluge site is down, so I can't ask on there.

---

### Post by sffvba[e0rt on 2011-02-10
Hi,

Unfortunately I don't have a solution for you... I can however sympathize as I have had this exact same problem with Deluge and maybe this bump can get this thread a bit more attention...


404

---

### Post by Vaphell on 2011-02-10
what would happen if you started torrent from zero (added to queue as if you wanted to download everything again), then closed deluge and then copied/moved your full copy of data in the exact place? Would deluge pick it up? maybe forcing a data check would do something too. Also do you have space reservation enabled, i think it would be necessary for it to work (torrent reserves everything it needs from the beginning and downloading merely fills the blanks).
I am sure it can be done, but you need to be creative :-)

---

### Post by sffvba[e0rt on 2011-02-10
> **Vaphell said:**
> what would happen if you started torrent from zero (added to queue as if you wanted to download everything again), then closed deluge and then copied/moved your full copy of data in the exact place? Would deluge pick it up? maybe forcing a data check would do something too. Also do you have space reservation enabled, i think it would be necessary for it to work (torrent reserves everything it needs from the beginning and downloading merely fills the blanks).
I am sure it can be done, but you need to be creative :-)

I have tried a lot of different things to get this to work over several days... and then out of a blue, I would create a new torrent, step by step like I did twenty times before and bam, it will work :confused: Then the next time, nothing...  Very frustrating, and several threads on several forums have come up with nothing... But I hope OP tries some of the things you have mentioned, maybe he has better luck than I had...

---

### Post by Vaphell on 2011-02-10
i tested it and it worked just fine in my 1st attempt

- i took one of recently downloaded tv series episodes and renamed it
- i loaded the torrent in deluge
- i waited for deluge to start downloading, paused DL and killed deluge
- i deleted started file and renamed the real thing back to take its place
- i launched deluge and forced recheck on the torrent

voila! 100%, seeding. Ratio is zeroed, but that is to be expected.

---

### Post by patelsagar on 2011-02-10
Hi, I have done so many times, but not with the program you are talking about.
Try Transmission or qBittorrent (qBittorrent is comparable to utorrent, it's the best out there I guess).

Give it a try and let us know :)

---

### Post by sffvba[e0rt on 2011-02-11
> **Vaphell said:**
> i tested it and it worked just fine in my 1st attempt

- i took one of recently downloaded tv series episodes and renamed it
- i loaded the torrent in deluge
- i waited for deluge to start downloading, paused DL and killed deluge
- i deleted started file and renamed the real thing back to take its place
- i launched deluge and forced recheck on the torrent

voila! 100%, seeding. Ratio is zeroed, but that is to be expected.

Most people don't seem to have this problem Vaphell... heck, before this thread I though I was the only one, and I had also tried this back when I was trying to seed... have not needed to nor tried this in a few months so I can't say it is still an issue for me (and I have changed distro's and clients several times now so I doubt this will effect me now)...

Would be curious to here back from OP if it worked for him though...


404

---

### Post by Eggness on 2011-02-14
Hey, sorry I didn't reply quickly.  I tried something similar and it didn't work for me.  I just ended up giving up on it and saying I'm not gonna seed on those torrents.  I would have tried Transmission, but it's not allowed on the tracker I use.  I'm not sure if qBittorrent is or not.  I really miss utorrent right now lol :P

---

### Post by Cas07 on 2011-03-22
The only way this might be solved is with debug logs posted on the Deluge support [forums]("http://forum.deluge-torrent.org/"). 

Also we will need more information about the steps taken to reproduce the issue, along with deluge and libtorrent versions.

---

