---
title: "Dynamic/Hot Backups"
date: 2009-09-26
forum: General Help
---

### Post by Richardljohnson on 2009-09-26
While I have used Linux for a while I have never really worked with backups. I am in a situation now that I need some advise on.

We use several systems at work that are VMWare 'packages' (xp virtual workstations and some Server 2003). They are running on a Windows server but my boss has agreed to upgrade to Linux (due to cost savings). I have been 'playing' around with Ubuntu 9.04 and got VMWare running fine. My problem is on doing backups. While we will do a mirrored drive for the 'packages', a seperate drive from the OS, I want to backup the 'packages' to a single drive also on the server for a 2nd form of protection. 

I want to run a backup of the running VMWare systems (packages) every 12 hours. My first few attempts have not been too good. In other words the size is correct but when I try and run them they fail. 

So here is my question.

Which automated, open source backup utility will do a dynamic/hot backup?

GUI would be good becuase this way I could teach someone else (the boss) how to check or recover if something happens while I am away.

Thanks,

---

### Post by blueridgedog on 2009-09-26
I would use rsync to synchronize a backup location with your package location.  There are gui tools available, but since it is a copy and not some sort of blob binary backup file, restore and use are trivial.  

Use could be as simple as:

rsync -av /packages/ /mnt/Backup_Drive/packages --delete --log-file=/path/to/your/logdir/$(date +%Y%m%d)_rsync.log

There are many other ways to do this, but this can easily be scheduled, executed and verified.

Good luck with Ubuntu, your project and the migration.

---

### Post by Richardljohnson on 2009-09-28
Thanks for the information.   I will try it also but after 3 days of testing I think I found my solution. BACKINTIME software appears to do what I want. I have found out that Windows thinks there was a power issue with you restart the backup but I can live with that. Plus it give me a GUI which I can screen shot for the boss.  Thanks, R-

---

