---
title: "rsync, hard links and copying  incremental backups"
date: 2010-02-09
forum: General Help
---

### Post by pwebguy on 2010-02-09
I have been using [this backup scenario]("http://www.mikerubel.org/computers/rsync_snapshots/") for about a year now and it works perfectly.

In a nutshell, I have a cron that runs the following:

1. rsync to copy mail folders from /home/vmail/ to /bkup/vmail/current/
2. use cp -al /bkup/vmail/current/ /bkup/vmail/`date +%m`/`date +%d`

So now, according to the tutorial I have a year's worth of data neatly stored with minimal disk usage due to the use of hard links.

I want to archive all of 2009 to another drive; if I use rsync on the /bkup/vmail/ dir with the -H or -l option to copy the backups to a separate archive disk, will that make a 1 to 1 copy of my archives (files and links to copies), or am I going to get a full copy of each directory? Is there a better way to accomplish what I am trying to do?

---

### Post by quixote on 2010-02-10
With -H (preserve hardlinks) and -l (copy symbolic links as symbolic links), the archive copy will be just like the daily backups.  I could see that being a problem when the copy is on a separate disk because presumably most of those links would be broken.  (I.e. the system has no way of knowing that a symlink pointing to, say, /home/someuser/photos/beautiful-pic is pointing to a file on another disk.)

So, don't you want a full copy of your whole backup?  rsync has an "archive" mode (-a) which includes a whole raft of options: ```
-a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
```  from the rsync man page.  If you type "man rsync" (no quotes) in a terminal, it lists what they all mean.

---

### Post by pwebguy on 2010-02-11
Yes, I am using the archive option, but, as you say, I was unsure how -a would handle the links since I was copying to another disk.

I did a couple tests; using -azilH as options, and it seems to work as expected. Looking back on this test, you are correct; the -l and -H are redundant. It seems I was over thinking.

I'll continue with this and post anything else interesting I find, but it seems that just the -a (archive) takes care of the problem.

---

### Post by quixote on 2010-02-11
Yeah, testing is the way to go.  I get very confused by rsync's ideas about links and find I have to see what it actually does.  For instance, the archive option preserves symlinks as symlinks, which, as I said, doesn't seem logical.  But, whatever works, right? :D

---

