---
title: "rsync copies symlinks as hardlinks"
date: 2010-01-16
forum: General Help
---

### Post by Humphreybas on 2010-01-16
Hey I'm using rsync to backup my laptop's home directory to my server.
It is the rotating backup system from here: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)
There are four folders on my server: backup.0 - backup.3  each containing one backup and all four are together +/- one time the size of my laptop's home directory (32GB) thanks to the rotating backup system with symlinks.

But I recently purchased a new hard drive for my server and want to use it partly as backup for my server. So now I have my primary hdd mounted as /home on my server and the secondary as /mnt/backup and it contains a copy of my /home.
But when I rsync /home to /mnt/backup the laptop backup files take 118GB (+/- 4*32). So instead of copying the symlinks in the backup.0 - backup.4 folder it just makes four folders with hardlinks.
The command I used was:
```
sudo rsync -av --delete /home/ /mnt/backup/
```and then I tried:
```
sudo rsync -alv --delete /home/ /mnt/backup/
```Both no luck... who can help me?

Edit: 
sorry for this message, I was confused with the whole hardlink softlink story.
The symlinks I was talking about are actually hardlinks so I should have used the -H flag to fix my problem (once I discovered it were the hardlinks I could easily find it in the man)
```
sudo rsync -aH --delete /home/ /mnt/backup/
```


(I changed the title in case anyone has this problem and did not read the solution in the man but googled it)

---

