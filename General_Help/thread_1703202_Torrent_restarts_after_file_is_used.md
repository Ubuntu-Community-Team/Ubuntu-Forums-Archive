---
title: "Torrent restarts after file is used"
date: 2011-03-09
forum: General Help
---

### Post by Sicadastra on 2011-03-09
Hello,

I'm always confused about this issue with bittorrent. The problem usually is that whenever I use the files, which are mostly audio files (that is, I play them), after they are downloaded, the torrent files restarts again. So I have to wait for the file again to finish downloading so I can seed.

Does anybody have the same problem?

Comments would be appreciated.

ETA: I'm using Transmission BitTorrent Client.

---

### Post by Vaphell on 2011-03-09
That should not happen, i do this with tv episodes all the time.
I suspect your audio player is so nice and helpful that it moves your downloaded files you try to play to some central place where music is kept (aka imports them) and as a result the torrent client sees the file is missing and starts it again. I may be wrong though. Does this happen with other file types?

Even if i am mistaken, the obvious way to prevent that is to copy files first to some other place and then play them.

---

### Post by slmouradian on 2011-03-09
I presume you are talking about freely distributed music, right?

---

### Post by Grenage on 2011-03-09
> **slmouradian said:**
> I presume you are talking about freely distributed music, right?

I'm sure he is.

> **Sicadastra said:**
> Hello,

I'm always confused about this issue with bittorrent. The problem usually is that whenever I use the files, which are mostly audio files (that is, I play them), after they are downloaded, the torrent files restarts again. So I have to wait for the file again to finish downloading so I can seed.

Does anybody have the same problem?

Comments would be appreciated.

What client are you using?

---

### Post by zenwalker on 2011-03-09
In case of transmission, this behavior does happen if you move the downloaded torrent files.

---

### Post by Sicadastra on 2011-03-09
> **Vaphell said:**
> That should not happen, i do this with tv episodes all the time.
I suspect your audio player is so nice and helpful that it moves your downloaded files you try to play to some central place where music is kept (aka imports them) and as a result the torrent client sees the file is missing and starts it again. I may be wrong though. Does this happen with other file types?

Even if i am mistaken, the obvious way to prevent that is to copy files first to some other place and then play them.

Copying the files would be my last resort since my disk space is quite limited right now even with the use of an external hdd.

I have no problem when it comes to downloading films though and watching them.

---

### Post by Sicadastra on 2011-03-09
> **Grenage said:**
> I'm sure he is.



What client are you using?

Sorry, I forgot to mention it. I'm using Transmission BitTorrent Client.

---

### Post by Grenage on 2011-03-09
I am guessing that, as previously mentioned, the client moves the files when the download is complete?  I've only used deluge on the desktop, and I don't recall that having a problem when playing active torrents.

That, or the transmission client has issues with not having exclusive access to a file.

---

### Post by Sicadastra on 2011-03-09
> **Grenage said:**
> I am guessing that, as previously mentioned, the client moves the files when the download is complete?  I've only used deluge on the desktop, and I don't recall that having a problem when playing active torrents.

That, or the transmission client has issues with not having exclusive access to a file.

Does the 'moves the files' means they are transferred to another location/folder? It doesn't though because that's the first thing I checked when it happened. The files are still in my Torrent Downloads folder that's why I'm confused why my client suddenly has some sort of blind spot. :(

---

### Post by Vaphell on 2011-03-09
backup few of your downloaded audio files for test purposes and check what happens with them when you try to play them - do they disappear from their original location? That would indicate that the audioplayer is to blame.
And if the files are still there - can you stop your torrent app downloads and force-check the torrent to pick up the files it thinks are missing?

---

### Post by rvchari on 2011-03-09
> **Sicadastra said:**
> Hello,

I'm always confused about this issue with bittorrent. The problem usually is that whenever I use the files, which are mostly audio files (that is, I play them), after they are downloaded, the torrent files restarts again. So I have to wait for the file again to finish downloading so I can seed.

Does anybody have the same problem?

Comments would be appreciated.

ETA: I'm using Transmission BitTorrent Client.

i ve never faced that problem. i never used bit torrent till date. i used to use u-torrent and run it thru wine. now i ve done away with that and am using deluge. it has a simple but effective user interface. you can find it on the software center.

further more, i ve organised it like this.
i have defined the folders that the torrent files will be downloaded. once it is finished, the client will move the downloaded (finished files) to another location i specified.
by keeping track on that folder i know how much has finished and how much is pending. after this, you can either delete the torrent (torrent only and not torrent with data) from the list so your pending list will be just the ones that have to be downloaded.

the finished torrent folder is again organised manually by me by sorting it and moving the files further according to caegory (music / video / software / others etc)
i keep my torrents and maintain like this.

in your case i think you must have asked bit torrent to move the files first. try to check if the finished torrent files are only moved or even the pending torrents are moved...

---

### Post by Sicadastra on 2011-03-09
> **Vaphell said:**
> backup few of your downloaded audio files for test purposes and check what happens with them when you try to play them - do they disappear from their original location? That would indicate that the audioplayer is to blame.
And if the files are still there - can you stop your torrent app downloads and force-check the torrent to pick up the files it thinks are missing?

I copied a certain album to another location and played it from there. I checked my torrent and it's working so I believe it's my client that has problems. :(

It also indicates that the restarted torrents are "corrupt" based on the client's torrent information. I guess I'll have to look for another client. 

Thank you for the help.

---

### Post by Sicadastra on 2011-03-09
> **rvchari said:**
> i ve never faced that problem. i never used bit torrent till date. i used to use u-torrent and run it thru wine. now i ve done away with that and am using deluge. it has a simple but effective user interface. you can find it on the software center.

further more, i ve organised it like this.
i have defined the folders that the torrent files will be downloaded. once it is finished, the client will move the downloaded (finished files) to another location i specified.
by keeping track on that folder i know how much has finished and how much is pending. after this, you can either delete the torrent (torrent only and not torrent with data) from the list so your pending list will be just the ones that have to be downloaded.

the finished torrent folder is again organised manually by me by sorting it and moving the files further according to caegory (music / video / software / others etc)
i keep my torrents and maintain like this.

in your case i think you must have asked bit torrent to move the files first. try to check if the finished torrent files are only moved or even the pending torrents are moved...

I think not separating the location for the incomplete and complete downloads contributed to my problem so I resolved that just now. Thank you for your reply because it gave me at least a chance for a solution.

---

