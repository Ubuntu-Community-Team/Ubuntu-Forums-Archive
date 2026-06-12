---
title: "Best sync method between Ubuntu and Windows"
date: 2009-06-29
forum: General Help
---

### Post by Twizzle on 2009-06-29
I am trying to work out what the best (and safest) method would be to sync my photos between three computers.

My desktop PC (Ubuntu 9.04) is my main PC and on this I store and edit all of my photos etc. Every time it is rebooted / shutdown an rsync script runs to back up / sync with my home server (Ubuntu 8.10 server edition)

I now have a netbook which is running Windows 7 (the wife prefers windows and I have a few Windows programs I need to run on it) and I would like to be able to view the photos on it both at home and away. As a result, I would like it to sync with the server and have the up to date photos on it. I will not be editing the photos on the netbook so I don't need netbook to server syncing but the other way round.

In an ideal world I would like a back ground task that realises when the netbook is on the network and pushes / syncs the photos onto the netbook but I am not sure how to do it.

Is there a program I can run on the server to do this and 'push' in this way, or is the best option to have the netbook run some sort of sync program in the background and just fail when the netbook is off line?

---

### Post by XCan on 2009-06-29
I think by far the easiest is if you run rsync on your netbook as well, perhaps as a startup script? There is a windows port for rsync called cwrsync [http://www.itefix.no/i2/node/10650](http://www.itefix.no/i2/node/10650) . If you really want the server to 'push' up the data, I guess you'll have to run some kind of daemon on the netbook, either ssh or rsync daemon.

---

### Post by jimv on 2009-06-29
Haven't tried this, but it looks promising:

[http://www.microsoft.com/prophoto/downloads/synctoybeta.aspx](http://www.microsoft.com/prophoto/downloads/synctoybeta.aspx)

Here's another program that I used awhile ago that was good called SyncBack.  There's a free version on this page:

[http://www.2brightsparks.com/freeware/freeware-hub.html](http://www.2brightsparks.com/freeware/freeware-hub.html)

---

### Post by Twizzle on 2009-06-29
XCan - thank you for that it looks very promising and is very flexible. Currently trying a quick sync to see how I get on.

jimv - thanks for the links. I have tried a number of windows sync programs so far but they all (including sync toy) have had the same problem, that they leave a small file on the server I assume to record something to do with the sync. The only problem with tihs is as my desktop PC is the 'master', the file is deleted everytime I sync that so it seems to try and sync the netbook from scratch again.

I will keep playing and trying tools that people reccomend - I was just wondering if any one was in the same boat and had come up with a good solution. So far the WIndows port of rsync is winning...

---

### Post by XCan on 2009-06-29
You're welcome! cwrsync actually works really well. I've been using it to sync down my workstation though ssh before I went all in Ubuntu at work and at home. :)

---

