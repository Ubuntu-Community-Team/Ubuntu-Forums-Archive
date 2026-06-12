---
title: "Why does my partition have 10 GB unaccounted for?"
date: 2009-12-29
forum: General Help
---

### Post by johnnydopefish on 2009-12-29
Hello,

I'm getting low disk space warnings so I deleted a bunch of crap but it seems that I'm working with 10 GB less space than I originally allocated.

Here's part of the output of 'df -h'

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              53G   35G   16G  69% /home
/home/johnny/.Private
                       53G   35G   16G  69% /home/johnny

```

Says 35 GB used, right?  Seemed like a lot more than made sense to me.  But when I do 'du -ch /home' (single-user system) here's the end of it:

```

25G	/home
25G	total
```

both du and baobob say I'm only using 25 GB.  That's a significant difference; surely it isn't a rounding error.  

Why is there a discrepancy?  Where'd that extra 10 GB go?

Thanks

---

### Post by drs305 on 2009-12-29
Have you emptied your Trash, including any trash owned by root that might be in your /home folder? 

I wrote a guide for exploring "lost" disk space - ways to find it and get it back. You might find an explanation there.

[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

Normally lost space is the result of undeleted trash, backups made to the wrong partition, or large log files. Since your issue is with the space on your /home partition, it probably isn't a log issue since these are normally written to a system folder.

---

### Post by sbsbessa on 2009-12-29
Just solved a similar problem described here [http://ubuntuforums.org/showpost.php?p=8576104&postcount=8](http://ubuntuforums.org/showpost.php?p=8576104&postcount=8)

It was in fact a backup that went to the wrong place as the external drive got mounted to a different location :S

---

### Post by johnnydopefish on 2009-12-31
Thanks for the replies; it wasn't anything having to do with trash or anything else on that guide.

On a possibly related note though, I've been using Transmission to BitTorrent a lot of stuff lately.  If I'm in the process of downloading something that says it's 10GB, does Transmission pre-allocate that memory and reserve it for the incoming torrent?  If it does, perhaps that's why I can't access the 10GB in question.

---

### Post by drs305 on 2009-12-31
> **johnnydopefish said:**
> On a possibly related note though, I've been using Transmission to BitTorrent a lot of stuff lately.  If I'm in the process of downloading something that says it's 10GB, does Transmission pre-allocate that memory and reserve it for the incoming torrent?  If it does, perhaps that's why I can't access the 10GB in question.

Good thought! A quick Google search seems to indicate Transmission does reserve disk space and this is a distinct possibility for your situation. I haven't used Transmission so I haven't experienced this problem.

I too would like to know from Transmission users how the space allocation works, and also what the effects of an aborted download might do to the space reserved (whether it remains reserved, how to clear it, etc). 

I didn't write about this in the Disk Space guide, but would very much like to include this as a consideration if we can get the details of how Transmission works.

---

### Post by johnnydopefish on 2010-01-02
I want to think Transmission is the culprit but unfortunately I had to reboot my computer after I finished downloading my torrents and deleting some of the content, which puts two variables in this equation.  Probably should have tried rebooting to begin with; now I'll never know what was responsible.  Here's the output I'm getting now:

df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              53G   29G   22G  58% /home
/home/johnny/.Private
                       53G   29G   22G  58% /home/johnny

```

du -ch /home

```

29G	/home
29G	total

```

Magically, both tools are reporting 29G used.  Oh well.

---

