---
title: "BitTorrent (Transmission) problem"
date: 2011-09-01
forum: General Help
---

### Post by gattz on 2011-09-01
For some reason I'm getting sloppy and inconsistent download/upload speeds. I'm still pretty new to Ubuntu and not familiar with this kind of thing so I'm not quite sure where to start. Right now I'm downloading a torrent with 8 seeders and I'm getting a really bad download speed. Other times torrents download incredibly fast with no problem.

The reason I believe there is a problem is because when I got to Edit > Preferences > Network >Test Port, it tells me the port is closed. Same thing for any port. I know this is probably a lame question but I would really appreciate some input from a knowledge member here. Thanks.

---

### Post by krytorii on 2011-09-01
I find that 6 dresses isn't very good, and dl speeds go up and down like mad no matter what. Try a more popular torrent with more seeders to see if its just that

---

### Post by Enigmapond on 2011-09-01
> **krytorii said:**
> I find that 6 dresses isn't very good, and dl speeds go up and down like mad no matter what. Try a more popular torrent with more seeders to see if its just that

I agree. Another possible solution is to forward the port on your router and making an exception in ufw for port 51413 and allow it although the first solution works better...then again as krytori stated...it just may be the seeders are few or have a low bandwidth. Try his solution to see. It's not the OS...I have the same speeds in both 'Doze and Ubuntu...always have.

---

### Post by gattz on 2011-09-01
I found some great guides on here and was able to solve the problem, I think. I was able to open the port and now the download is going fine. It only has 10 seeds so it's not blazing or anything, but I'm trying to download something really obscure so I pretty much have to go with this torrent.

---

### Post by haqking on 2011-09-01
well seems you have answered your own question about port forwarding etc.

however with torrents always remember that your DL speed will always be dependant on the seeders, not just how many but at what speed they throttle at.

you can have a 50M conneection and 1000 seeders all online, but if they all throttle you may still only download at a slow speed (though unlikely).

There is also encryption, here in the UK with ISP traffic monitoring it is best to force encryption for all torrents, a necessary but often speed hindering act.

---

