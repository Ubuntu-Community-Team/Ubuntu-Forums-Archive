---
title: "How to share torrents profile if dual booting?"
date: 2009-11-10
forum: General Help
---

### Post by retano on 2009-11-10
Hi all, 

Currently I use dual boot with Ubuntu 9.10 and Win Vista
Successfully shared profiles for my FF3.5 and TB2, but got stuck with utorrent. 
All torrents reside on NTFS partition (first OS was Win)
Is there any chance to get same profile for torrents (even changing client for win?), keeping all torrents in the same folder, settings, statistic of upload ratio etc in dual boot?

Thank you!

---

### Post by cyclobs on 2009-11-10
you can.

but it's hard and start up is slow between switching them.

basically you make a symbolic link to the windows config file and also set up a symbolic link to your windows download location so that when utorrent loads the torrent files it'll also load the downloaded stuff.

but as i said. every time you switch utorrent will recheck the data and such before continuing to download

---

### Post by retano on 2009-11-10
Not sure if µTorrent is available for Ubuntu, do you mean different torrent-client?
Maybe you can point me a link to info so I can try there....

---

### Post by madhi19 on 2009-11-10
This might sound like overkill but why not use an old computer as your files server/seed box. You set up a few shared folders on a strip down ubuntu install and manage to whole thing via remote desktop. That way whatever you do with your main rig will not affect long big download you might have going on.

---

### Post by retano on 2009-11-10
That is a cool solution, but unfortunately right now I am stick with one PC :(

> **madhi19 said:**
> This might sound like overkill but why not use an old computer as your files server/seed box. You set up a few shared folders on a strip down ubuntu install and manage to whole thing via remote desktop. That way whatever you do with your main rig will not affect long big download you might have going on.

---

### Post by retano on 2009-11-10
anyone?

---

