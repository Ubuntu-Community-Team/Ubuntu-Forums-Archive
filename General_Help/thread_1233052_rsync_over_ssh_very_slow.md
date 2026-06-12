---
title: "rsync over ssh very slow"
date: 2009-08-06
forum: General Help
---

### Post by bronkeydain on 2009-08-06
I am using rsync over ssh to backup my music files over the network. I have about a 150GB of music (mainly mp3) to sync. I think it is so slow because of the overhead SSH encryption generates.

Right now I can transfer about 4.3 MB per minute, about 260MB per hour.
My LAN is 100Mb. I can see transfer speeds up to 135KB per second, but it does so at intervals and then back to 0.

The command I use:

rsync -av -e "ssh -p 1212" myuser@myserver:/media/MUSIC /media/160GB

I was wondering if anyone has experience with rsync over ssh and if there would be anyway to speed this transfer up, using proper security?
I have searched this forum and don't find a lot of info on this matter.

Thanks in advance!

---

### Post by barnex on 2009-08-06
Although I cannot pinpoint the reason for your problem, I can tell you that rsync over ssh is generally very fast. I get about 10MB/s with less than 1% cpu load. So don't ditch rsync, it must be possible to get it running very fast!

btw, I have a backup script that loosely looks like this:

rsync --archive --delete-after --progress --stats --human-readable --one-file-system --max-delete=1000 /home/user [email]user@server.org[/email]:/backupdir

hope this helps.

---

### Post by bronkeydain on 2009-08-06
Thanks for your quick reply Barnex. At least that gives me the confidence to dive into this matter.
I will have a close look at your script this afternoon, but first things first... lunch (yummm)

---

### Post by bronkeydain on 2009-08-06
I checked all the parameters that you use. I thought possibly the delete-after or the one-file-system option might make a difference so I tried the following command:

rsync --archive --delete-after --progress --stats --human-readable --one-file-system --max-delete=1000 -e "ssh -p 9753" myuser@myserver:/media/MUSIC /media/160GB

The stats are handy as it gives me the transfer speed but unfortunately it is still slow,
It is not a hardware issue, or at least not the LAN as other transfers (i.e. Samba) go much faster. 
I get about a 60/kB per second transfer rate with rsync over ssh.

Could this be because of a slow processor (AMD Athlon 2800)? Any other suggestions anyone?

Thanks again.

---

### Post by bronkeydain on 2009-08-06
It seems that some files (in this example the Jpg) transfer much faster than others.
The jpeg in this example has transfered at 6.86 MB/s and most mp3's at around 50 or 60 kB/s

```
MUSIC/MUSIC/ALL MUSIC/Música + Pelis- Julio 04/Michael Stearns/Steve Roach, Kevin Braheny, Michael Stearns - Desert Solitaire/Folder.jpg
       7.17K 100%    6.84MB/s    0:00:00 (xfer#21, to-check=17947/22043)
MUSIC/MUSIC/ALL MUSIC/Música + Pelis- Julio 04/Michael Stearns/Steve Roach, Kevin Braheny, Michael Stearns - Desert Solitaire/Steve Roach, Kevin Braheny & Michael Stearns - Cloud of Promise.mp3
       7.93M 100%   55.09kB/s    0:02:20 (xfer#22, to-check=17946/22043)
MUSIC/MUSIC/ALL MUSIC/Música + Pelis- Julio 04/Michael Stearns/Steve Roach, Kevin Braheny, Michael Stearns - Desert Solitaire/Steve Roach, Kevin Braheny & Michael Stearns - Desert Solitaire - 01 - Flatlands.mp3
       5.80M 100%   48.01kB/s    0:01:57 (xfer#23, to-check=17945/22043)

```

Not sure why this is, could it be it requires some tweaking (buffers or something)?

---

### Post by bronkeydain on 2009-08-07
I have searched alll sorts of forums to no avail. I checked my logs, network config, all looks fine to me.

Everyone is having faster speeds than me. 
If I (s)ftp the same files over it transfers at 300KB/s, and rsync/ssh I get 60KB/s on larger files (these are all compressed too but I switched of compression of rsync for that reason). The smaller files (text files, and Jpegs) do transfer at a much faster rate. 

Not sure what to try next... I could FTP the whole lot over and then use rsync to keep them synchronized, but that is a workaround rather than a fix.

:confused:

---

### Post by bronkeydain on 2009-08-07
Actually I realise that FTP-ing at 300KB/s on a LAN is also very slow so will investigate further.

---

### Post by bronkeydain on 2009-08-09
I was doing some tests this weekend from home and suddenly I am getting really fast transfers, close to 10MB/s which is what you would expect from a 100Mb LAN.

The only difference with the situation before is that the only Windows machine on the network is switched off! I am sure that machine is riddled with infections of all sorts and is probably generating a lot of network traffic...

---

