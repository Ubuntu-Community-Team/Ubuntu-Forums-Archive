---
title: "Ubuntu backup/sync checklist"
date: 2009-07-05
forum: General Help
---

### Post by morganpatrick on 2009-07-05
I have a desktop and a laptop and I would like to keep them totally synchronized. This includes my localhost at /var/www and all my settings for all my programs.

Every time I reformat a computer I forget to do one thing or another. In this case I switched both computers to ubuntu and lost all my bookmarks in the process.

Is there a good checklist, method or app to ensure that you copy over absolutely everything you need?

I would like to keep my current configuration going forward, upgrading to the newest ubuntu years into the future. Even if my laptop dies, I would like to restore my backup and have essentially the same system on a new piece of hardware (minus hardware drivers obviously). What is the best way to keep my system synched, backed up and relatively portable?

---

### Post by binary10 on 2009-07-05
i use rsync, it does differential syncs.. i find it easy to restore... u can backup partition by partition.. and you can get to your files pretty easy. of course disk space is dup'd but not too much of an issue with usb disks these days.

flags i use are 

 rsync --archive --delete --hard-links --numeric-ids --stats -i --human-readable --one-files-ystem /<partition>/   /mnt/usb/<partition>/

subs <partition> for what u want to save

---

### Post by morganpatrick on 2009-07-07
Do you have any experience with conduit? I have downloaded it but haven't used it yet. It looks graphically appealing but I wonder if it works better or worse than rsync.

---

### Post by dka on 2009-07-07
for backups rsync is definitely a nice tool.  While I have never used conduit, I have found a nice bash script using rsync attached to a cron job was more than enough for me. 

For keeping /var/www/ synchronized it might be easier to subversion.  Subversion is a version control system that allows you to checkout files, make revisions and check them back in.  SVN is just another of many tools.

---

