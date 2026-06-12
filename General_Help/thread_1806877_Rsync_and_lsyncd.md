---
title: "Rsync and lsyncd ??"
date: 2011-07-18
forum: General Help
---

### Post by minerbog on 2011-07-18
Hi all,

Can't really find much on this from Google so I thought I would ask the masses of intelligent peeps at Ubuntuforums.org!!! :)

I'm setting  up a backup server at work running Ubuntu 10.04 server. The desktop machines run Ubuntu 11.04 desktop so I'm looking at backing up via either rsync or lsyncd. Its just I cannot really find out what the difference is?

Although this is being set up as a backup server I was also looking at trying a syncing set up similar to dropbox for the developers here to sync their work.

Which one should I use? Or is there something better?

Many Thanks

Gavin.

---

### Post by malleeblue on 2012-09-09
Hi minerbog. You would use both. Meaning, you would use lsyncd to run at startup, and lsyncd would be set to use rsync when it detected changes in any of the folders you asked it to monitor.

I've recently set up lsyncd to monitor about 6 folders on my computer that backs up to another always-on computer on my LAN. I've mounted the folders locally using cifs, and the Dropbox-like, instant replication is awesome. It took me a while to set it up and iron out the kinks (most of which were caused by my newbieness), but I'm loving it. One drawback that I don't know how to solve is versioning. I'd love it if my setup would keep, say, 100 older versions of files. None of my stuff is that critical though, so I can live without it, but if I ever find out how to do that with my setup I'll be the happiest Ubunter around.

---

