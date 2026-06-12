---
title: "Slow bittorrent dl rates"
date: 2011-05-09
forum: General Help
---

### Post by Dookert on 2011-05-09
Hey all,

After searching around in the forums and across the world wide interweb, I have found no real answer to this question. Downloading torrents via a ubuntu client is ridiculously slow compared to the same download made simultaneously on the same network via a windows machine. Right now I am downloading a 1.7 GB torrent on my windows machine at approx. 370 kbps. The same exact torrent started on my ubuntu box 10.10  crawled its way forward to 50 kbps after about 5 minutes. Within 1 minute of starting it on the windows machine it had peaked, at the afforementioned speed. No upload or download limits have been set for either, and for some reason deluge on the linux box was uploading faster than it was downloading, but never comming close to how fast the windows client (bitlord) had reached with minimal effort.  I have found this to happen across multiple ISP's and states via  cable modem  quite consistently. 

I had already tried port forwarding and all that crap last year to no avail. Why do ubuntu clients seem to need all this tweaking to get good speeds when there are 8000 plus seeders available and their windows counterparts are blazzing past them so fast its pathetic? Its seriously no comparison, and something as simple as a bare bones client like deluge should FLY when there are 8000 seeders. I shouldnt have to open ports, click this box, edit this config file, blah blah blah. Something so simple should just work, with no configuration whatsoever. Almost everything your average computer user needs to use works so effortlessly with ubuntu but this one is just annoying. I dont even bother with my linux machine to download torrents. I just open up my windows laptop cause its so much faster


what gives?

---

### Post by 3 frags left on 2011-05-09
Excuse me, but are you using Transmission? In that case, haven't you let Temporary Speed Limits enabled by accident? Because I, as well as all Ubuntu users, never had such a problem...

---

### Post by Dookert on 2011-05-10
> **3 frags left said:**
>  I, as well as all Ubuntu users, never had such a problem...

This problem has arisen in multiple posts, across multiple forums, and on multiple distros. 

Here is one example of many:

[http://ubuntuforums.org/showthread.php?t=1316190](http://ubuntuforums.org/showthread.php?t=1316190)

Also, to clarify, my thread says that I am using deluge, not transmission.

Regardless, this is not the problem. It maybe something I havent set yet, but port forwarding, which is the first thing people have suggested, does not seem to be the problem. I have configured deluge hooked directly to the cable modem as well. Either way, I can see the torrent not downloading at all because of a blocked port/ports, but not that it is sitting at around 50kbps after crawling up to that speed over a period of time, whereas windows rockets to 370 in 1 minute tops.

---

