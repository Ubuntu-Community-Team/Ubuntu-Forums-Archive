---
title: "rsync problems - needless re-uploads"
date: 2010-01-06
forum: General Help
---

### Post by Canyonero on 2010-01-06
My brother-in-law and I have a deal worked out where he has some space on my computer and I have space on his that we use for off-site backups. We each worry about our own files, leaving the other to deal with their own backups.

The problem I'm running into is that his system has had to change many times, often very small changes. He has changed ISPs a few times, moved my backup directory once or twice, taken a system offline because of potential flooding issues (which is a big reason he wants to back up to my machine). I think the reason the ISP changes have caused problems was that one ISP (a municiple Wireless service) had a static IP, so he forwarded his own .com address to the machine. The new ISP has dynamic, so he switched to a dyndns address. My system sees a different address and assumes it's a different machine.

Every time something changes (ANYTHING changes) my system wants to start over, re-uploading everything from scratch.

In the most recent case, I came to realize that the 200GB I had for my backups wasn't enough. I keep identical drives on both machines, keeping things simple. I bought a couple 1TB drives to expand just before Christmas. To cut down on bandwidth overload, I backed everything up to one of the new drives on my machine, then hooked the other drive up and rsync'd everything on the one drive to the other. Then at Christmas I gave him the new drive that was to go on his machine, with almost 300GB of data on it.

When he got back and hooked it up, I tried a dry-run (-n) and it was showing that it wanted to re-sync everything. At almost 300GB, that could take weeks.

My question is, not knowing a ton about rsync, how can I force this thing to accept that the files on both ends are the same and don't need to be re-synced?

Here is the command I am running:
```
rsync -arv --delete -e "ssh -i /home/myuser/.ssh/key_dsa" /backup/myuser/Backups remoteuser@remoteserver.com:/home/remoteuser/Backups
```

Once I know it's working, I plug that into a cron script, removing the -v option

---

