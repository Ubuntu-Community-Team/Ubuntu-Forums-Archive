---
title: "Unison Questions."
date: 2012-03-20
forum: General Help
---

### Post by Roasted on 2012-03-20
I've been recently tinkering around with some sync GUI's and I ran into Unison. I'm kind of curious, it doesn't appear as if Unison is based directly on rsync, as they cited on their web site as having their own core that they utilize that is "similar" to rsync, but not exactly like it. As a result, I'm kind of curious how Unison works. Is there a way to add custom flags to it, like you can with rsync? If not, what is its default behavior? Will it preserve time stamps, permissions, owner, group, etc.? 

The only other concern I have about Unison is I just set up a test to see how it went. I created 2 folders on my Desktop, named Source and Destination. I created a bunch of blank files and ran the sync, okay fine, Destination is now populated. Great.

For kicks, I deleted everything in Destination and ran it again, but it prompted me with an error, citing: 

```
Warning - The root of one of the replicas has been completely emptied. 
Unison may delete everything in the other replica.
```

If I hit go, everything in Source deletes. I'm not sure what Unison's goal is, but this is kind of disappointing, as I could see users accidentally hitting the wrong thing in the event their Destination folder changed for whatever reason. On the flip side, rsync in this case would simply rsync everything back over.

Not trying to down Unison at all, but I'm just trying to understand this behavior, among an array of other things about it, such as custom flags, etc. Also, is there any way to automate Unison jobs, whether by GUI, Cron, or Startup Applications?

Thanks for the insight!

---

### Post by Habitual on 2012-03-20
vi  ~/.unison/roasted.prf
```
# Unison preferences file
root = source
root = destination
perms=0
```and run it with:
```
unison roasted -batch -ui text -auto
```shell script for the cron:
```
#!/bin/bash
unison roasted -batch -ui text -auto
```save it as say ~/uniroast.sh
```
chmod 770 ~/uniroast.sh
```add to cron with the desired parms.

~/uniroast.sh


I don't know about the error,sorry.


HTH.

---

### Post by Bucky Ball on 2012-03-20
Perhaps just don't hit go then repopulate target with source. Doesn't really satisfy your curiousity re Unison's behaviour, though.

---

### Post by LewisTM on 2012-03-20
Go [here]("http://www.cis.upenn.edu/~bcpierce/unison/docs.html") to learn all there is to learn about Unison.

It's my favorite synchronization tool. Unison is CLI but package unison-gtk contains a GUI. Everything is usually setup with .prf files located in ~/.unison. Jobs can be automated if you are confident; the GUI is useful for previewing changes and telling it in which direction to apply them.

For instance this command will open backup.prf, force all changes from the '/home' root to be transferred to the target and approve all operations
```
unison backup -force /home -batch
```

It uses the rsync's algorithm for comparing files and writing changes only.

---

### Post by Roasted on 2012-03-20
> **LewisTM said:**
> Go [here]("http://www.cis.upenn.edu/~bcpierce/unison/docs.html") to learn all there is to learn about Unison.

It's my favorite synchronization tool. Unison is CLI but package unison-gtk contains a GUI. Everything is usually setup with .prf files located in ~/.unison. Jobs can be automated if you are confident; the GUI is useful for previewing changes and telling it in which direction to apply them.

For instance this command will open backup.prf, force all changes from the '/home' root to be transferred to the target and approve all operations
```
unison backup -force /home -batch
```

It uses the rsync's algorithm for comparing files and writing changes only.

If it uses rsync's algorithm, why does it nuke my source in my small experiment above? 

I have to be honest, that scares me to even use Unison with critical data. I've **never** seen a sync program of any sort do that. Am I, somehow, using it improperly? Or misunderstanding?

---

### Post by dcstar on 2012-03-20
> **Roasted said:**
> I've been recently tinkering around with some sync GUI's and I ran into Unison. I'm kind of curious, it doesn't appear as if Unison is based directly on rsync, as they cited on their web site as having their own core that they utilize that is "similar" to rsync, but not exactly like it. As a result, I'm kind of curious how Unison works. Is there a way to add custom flags to it, like you can with rsync? If not, what is its default behavior? Will it preserve time stamps, permissions, owner, group, etc.? 

The only other concern I have about Unison is I just set up a test to see how it went. I created 2 folders on my Desktop, named Source and Destination. I created a bunch of blank files and ran the sync, okay fine, Destination is now populated. Great.

**For kicks, I deleted everything in Destination** and ran it again, but it prompted me with an error, citing: 

```
Warning - The root of one of the replicas has been completely emptied. 
Unison may delete everything in the other replica.
```

**If I hit go, everything in Source deletes**. I'm not sure what Unison's goal is, but this is kind of disappointing, as I could see users accidentally hitting the wrong thing in the event their Destination folder changed for whatever reason. On the flip side, rsync in this case would simply rsync everything back over.
.........

That is **exactly** what it is supposed to do - it **synchronises** both places to be identical.

**You** have to learn and understand what sort of synchronisation **you** want.

---

### Post by Roasted on 2012-03-21
> **dcstar said:**
> That is **exactly** what it is supposed to do - it **synchronises** both places to be identical.

**You** have to learn and understand what sort of synchronisation **you** want.

How does it determine what syncs where and how? Is it by time stamp and which ever folder has the newer stamp is the "target" of the two folders to sync?

If that's how it works, it at least makes sense as to why the Source would get deleted, because once I deleted everything in Destination it effectively changed the time stamp on the Destination folder to be newer... Hmm...

If that's the case, I at least applaud the tool and can see its uses, but it's not exactly something I would use in my backup scenario. I need an A to B solution, not necessarily one that could flip A to B around and potentially be B to A if I don't watch it carefully.

---

### Post by Habitual on 2012-03-21
Roasted, 

Well, I'd like to suggest a new 2nd root as destination2 (if you have the disk space) and work through the tips we have given you.

and please have a look at [the manual]("http://www.seas.upenn.edu/%7Ebcpierce/unison//download/releases/") for your version.

[The mailing list]("http://www.cis.upenn.edu/%7Ebcpierce/unison/lists.html") may also be a more appropriate medium for "under-the-hood" questions about unison.

Have a Great Day!

---

### Post by kjohri on 2012-03-21
First, Unison is a two-way synchronization tool. If some files change in the first host and some other files change in second, after synchronization both hosts have the latest files. rsync is more of an advanced copy command, synchronization is one way.

Unison keeps track of the contents of the files. So, if a file is modified since the last synchronization at a host, Unison knows that the file has been modified and synchronizes that file at the other host. If you modify a file at both hosts and try to synchronize, Unison figures out a conflict and lets the user decide which file should be treated as "final". And if you delete a file (or files) at one host, Unison takes it that the file is not required, and deletes at the other host.

It is possible to use backup options, so that files that are overwritten or deleted are backed up somewhere.

[http://www.softprayog.in/tutorials/synchronize-files-advanced](http://www.softprayog.in/tutorials/synchronize-files-advanced)

---

### Post by Roasted on 2012-03-21
I do remember one case where I needed something like this in a specific environment. I just ended up coming up with two different rsync commands. One went one way, the other went the other way, which kind of mimic'd what Unison seems to do.

So, my apologies for that. Nonetheless, Unison sounds like it has a nice feature set, but that it's not quite the best "home backup" for Grandma who could easily get confused over something like that. I mean, I work in IT and I still got "what the?" over it. Then again, maybe it's just me, and maybe granny would have something to say about it. :lolflag:

---

### Post by erngab on 2012-03-24
If I understand well Unison is designated for synchronization not designated for backup.
I want to backup 14GB of data (PlayOnLinux) in one direction.
 Backups are not identical, if I do it with gsync or with Unison.
When I made backup with gsync, when start program (Photoshop) run with a mistake.
Backup made with Unison is OK program run well no mistake.
So I need some possibility of auto Unison sync-backup in one direction.

I tried it with backups
 w.prf:
 ```
# Roots for synchronization 
root = /media/sdb1/Desktop/a.tmp
root = /media/sdb1/Desktop/b.tmp

# keep backups 
backupdir = /media/sdb1/Desktop/c.tmp
```But in c.tmp I get the difference of a a.tmp - b.tmp synchronization.
In c.tmp I should get a a.tmp or result of a.tmp - b.tmp synchronization not a difference.
Now I imagine that c.tmp be my backup (PlayOnLinux backup) - whether if is it possible.

Command that you gave earlier is good for auto synchronization
unison w -batch -ui text -auto

---

### Post by Roasted on 2012-03-24
I understand. That makes more sense if unison was meant from simply syncing directories together versus an actual backup. Rsync can be used in the same demeanor yet it can definitely be used as a backup as well (best thing for a backup in my opinion) which is likely why so many Rsync GUI programs use it for the core (grsync, duplicity, deja dup, I think lucky backup uses it as well). But considering unison acts in more of a two way fashion I agree it takes away from the "backup" category a bit. At any rate, thanks for the insight guys!

---

