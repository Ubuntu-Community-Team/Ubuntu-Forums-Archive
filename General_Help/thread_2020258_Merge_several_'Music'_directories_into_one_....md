---
title: "Merge several 'Music' directories into one ..."
date: 2012-07-08
forum: General Help
---

### Post by Bucky Ball on 2012-07-08
Hi all,

I have used Unison and it is terrific ... if I want to sync two directories. The situation I have now, though, is this:

I have three separate Music directories which I want to merge into one. A couple are over 30Gb of music and similar, but there's anomalies like a folder for a particular artist has five albums on one machine and seven on another, for instance. To find the differences manually would be like finding the proverbial needle in the haystack.

So, the aim is to merge two of the music folders - one on an external drive, one on a desktop - onto the external drive, then merge the resulting merged music directory with a music directory existing on a third machine. 

Once I've emerged from the merging (!) I want to plop the lot on a networked PVR/media player so all the machines in the house can access all the music in it! Sweet.

Any ideas of the appropriate merging software (I've hunted but found nothing to exactly fit this) please fire away. Any improvements on my plan also welcome. ;)

---

### Post by Merrattic on 2012-07-08
I can't see any simple way without some serious scripting to do the tricky bits, they probably require human intervention, but don't see why an **rsync (grsync for gui)** or even incremental** cp** command [ **cp -urvp /pathto/fileslocation/* /pathto/backup/directory/ ] **wouldn't do it? (-u update only new or changed files, -p preserve file attributes, -r recrusive directories)

The merge would have to be on the basis of: "if not there copy it, if is there don't copy"

You could use a program like **meld** for comparison purposes

Once you have control, I don't see why you couldn't merge each set directly to the third machine, as opposed to the intermediate merge?

(Sorry never used unision, but guessing it can probably do all the above already?)

---

### Post by Bucky Ball on 2012-07-08
Cheers.

Unison creates two identical directories so not really. I am fooling around with Meld now. It seems good but can't get it to do the required process automatically. Wouldn't mind manual but there's heaps of stuff there. (Also finding Meld a little confusing so slowly looking through a few HOWTO sites as I'm trying to do four other things at the same time.)

Maybe I'll start looking into coding it but prefer not to bother and use a GUI. That might not be possible ...

Could merge everything directly to the third machine but it would be over a wireless LAN (could but don't want to). That's where the external drive comes in. ;) Kinda the 'physical link' between the three /music directories.

I have just realised I could use Unison for the first merge between my desktop and the external drive as they are almost identical anyway and that's fine. Hmmm, thinking this could be done with Unison because the collection on the third machine is almost the same, too!

So, once all merged and finally dumped on the PVR/media player I can delete the collection from the computers and keep the one on the external drive for backup as they'll all be identical (on all four devices). Yea, that should do it. Will report.

---

### Post by Merrattic on 2012-07-08
This has reminded me I really should back up my music collection on my server ;)

---

### Post by Bucky Ball on 2012-07-08
Unison would be handy for that as it will make your local music directory and the one on your backup device identical. If the one on your local machine then changes the next time you sync the changes are written to the external directory so it matches.

The main problem I found with it, and maybe there's a workaround if I dig, if that if you delete files, say, from one directory, because you genuinely don't want them, if they're still in the backup they're written back. I'll keep looking at that.

---

### Post by Merrattic on 2012-07-08
That's why I like the control of just going "one way" :)

---

