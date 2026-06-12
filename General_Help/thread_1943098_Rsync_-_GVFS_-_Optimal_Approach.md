---
title: "Rsync - GVFS - Optimal Approach?"
date: 2012-03-18
forum: General Help
---

### Post by Roasted on 2012-03-18
I set up a backup server at my parent's house so their stuff would automatically back up at a specific time. I was doing a backup earlier once I had it set up to make sure it was good and I used the --progress flag in terminal. It almost looked like it was looping, as the output didn't look normal. A quick search revealed it was pushing .gvfs to the backup server, which was a HUGE folder. It looked like it had cached everything, because within the .gvfs folder looked like a typical home directory that had all of the other stuff there too. It was strange, almost like a mirror effect.

To say the least, .gvfs became a concern that maybe I should avoid backing it up. The other day I had been curious about rsync GUI's and I remember one having a "do not leave file system" flag, which turned out to be GRsync. The terminal output suggested it was -x, and the man page of rsync confirmed it. Okay, fine. But what does do not leave file system mean, exactly? Is it referring to .gvfs where it won't touch .gvfs when the rsync is ran?

Is that to say:

rsync -ax /home/jason/ jason@192.168.1.150:/media/NAS/jason/
instead of
rsync -a /home/jason/ jason@192.168.1.150:/media/NAS/jason/

Would ensure that the rsync command wouldn't touch gvfs? 

In fact, I even remember putting --exclude=.gvfs tags in some of my rsync commands to avoid .gvfs on prior setups. Would the magic -x be the ticket to ensuring .gvfs doesn't get touched?

---

### Post by Roasted on 2012-03-19
Further reading has revealed the answer on AskUbuntu.com. I had always known of AskUbuntu but never used it, so I tried my luck and a user responded confirming the above suspicions: 

[http://askubuntu.com/questions/114165/rsync-gvfs-questions](http://askubuntu.com/questions/114165/rsync-gvfs-questions)

I'm just a little baffled as to why more people don't talk about -x or use it in examples when helping other users.

I mean, think about it like this. You have a laptop, and you have a backup server. Your folder on the backup server is called "storage", let's say. So you are rsyncing data, things are great, etc., then one day you notice the rsync is taking exponentially longer, only to find out you're duplicating the data:

Server:
/media/storage/data
/media/storage/data/.gvfs (gvfs including all of the data on the line above)

So you have, 1 2 3 4, and 1 2 3 4 + .gvfs 1 2 3 4. Eh?

If that's the case, and if it's that easy to accidentally duplicate all of the data, I'm just wondering why -x isn't more prominently discussed. More often than not, as I said in the link above, I see -av at most being used, which is of course archive and verbose. Why not -avx?

**_EDIT_** - Imagine that, there's an rsync IRC chat. I asked in there and their response was the -x flag cannot read it enough to tell that .gvfs is a separate file system. As a result, their vote is to simply exclude it as best practice. That said, I'm glad there's a solid answer.

In short, my rsync command will be sitting in cron scheduled to run at 7 PM every day, listed as:
rsync -a --exclude=.gvfs /home/user/ user@192.168.1.150:/media/NAS/user

rsync = core command used
-a = archive, keeps same owner, perms, group, time changes, etc
--exclude=.gvfs = excludes .gvfs from backup, pretty essential if you're rsyncing a home directory
/home/user/ = the home directory of the user in question
user@192.168.1.150: the file server in which user is backing up to (note, ssh keys are already in place so no need to password authenticate)
/media/NAS/user = location on file server where the home directory contents will be backed up

The only question I have now is, I noticed in 12.04 Beta I have on my laptop, .gvfs isn't located in /home/user, but actually in /home/user/.cache. Is gvfs going to be permanently located in .cache in the future? Do any other distros do this?

---

