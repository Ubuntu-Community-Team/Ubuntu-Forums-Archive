---
title: "/usr/bin/X11 gone wild"
date: 2012-04-09
forum: General Help
---

### Post by F35 on 2012-04-09
I have been running Ubuntu 11.04 for a while.  I now notice that I have a lot of disk storage being consumed at /usr/bin/X11.   My assumption is that this space is some type of stranded cache from my use of xrdp (remote desktop).  There are currently about 20 X11 nested folders, each folder having a virtuoso-t file (9.7 mb).

Anyone know if I can safely delete these?

---

### Post by F35 on 2012-04-10
Here are more files that are part of each nested X11 folder:

net.samba3
net
rpcclient
smbcacls
smbget
smbclient
smbpasswd
gdb
cinelerra
Xvnc4

It appears that each folder accounts for 259 MB, combining for 5 GB of disk space dedicated to this.  There are 20 levels of nested x11 folders currently.

Currently, each X11 folder has exactly the same creation date and time, so my guess is these folders were all created at the same time rather than one after another.  

If that is true, that blows my original theory that these might be generated each time a new XRDP session is initiated and then stranded by somehow not exiting properly.  There must be another reason why this issue has occurred.  

So, can anyone advance a theory as to why this would have occurred on a specific date (approximately 2 days ago) and is it ok to delete all these nested folder (I assume I should keep the top level X11 folder)?

---

### Post by F35 on 2012-04-10
After more investigation, I have found a second computer with exactly the same issue.  This computer shows it happened about 5 days ago.  To me, it is looking more like it occurred with some update download.  Since I now show two computers exhibiting the same thing, there must be others who are experiencing this.

---

### Post by scradock on 2012-04-11
> **F35 said:**
> After more investigation, I have found a second computer with exactly the same issue.  This computer shows it happened about 5 days ago.  To me, it is looking more like it occurred with some update download.  Since I now show two computers exhibiting the same thing, there must be others who are experiencing this.
This is happening for me in oneiric, one install checked so far. I have never used XRDP, so it doesn't arise from that...

Further observations: the top-level /usr/bin/X11 is marked as a link; it is linked to itself! This implies that there is in fact only one X11 folder, that is linked so that however far you go there is always a folder called X11. No need to worry about wasting space, though I am also curious as to why this is necessary.

It's also there in Precise...

---

### Post by F35 on 2012-04-11
...wasting space...

I discovered this X11 issue while performing a backup.  I saw a very large consumption of space (about 11 gb) being used just for /usr/bin.  That is how I discovered it.  I agree that it says it is a link (in Nautilus, it says Link to folder), but I feel like there is a large amount of wasted space being caused by this.

---

### Post by dmacm on 2012-07-13
I am having the same Issue on an ASUS ux32vd laptop. Is it safe to delete the nested directories?

---

### Post by jelcoward on 2012-09-05
Ubuntu 12.04 64bit

I have the 'nested' X11 folders too. I only looked because someone at vanlug posted a question about it wondering if it was causing him some slow downs.

I also have slowdowns - to the point of hangs - that seem to be related to the gui (going to shell and coming back fixes it).

Has anyone got any thoughts please?

Cheers

Jel

---

### Post by SantaFe on 2012-09-06
Found this link here: [http://ubuntuforums.org/showthread.php?t=829402](http://ubuntuforums.org/showthread.php?t=829402)

Someone said it's just a Symbolic link & shouldn't be taking up much if any space.  If you look at it in Thunar, it does show the Symbolic Link icon on it.  Just checked the size. "1 item, totalling 1 byte" ;)

---

### Post by shnshn52 on 2012-09-07
In the good(bad) old days of X11, programs that used X (GUI-based programs) were placed in /usr/bin/X11 while command line programs were placed in /usr/bin.  Nowadays this distinction is not made anymore and so X-based programs are just left in /usr/bin.  However to maintain backward compatibility with older programs that may expect to find X-based programs in /usr/bin/X11, the sym link 
     X11 --> .
is created in /usr/bin.

---

### Post by cryptotheslow on 2012-09-07
Interesting explanation :)

And as already stated, it's not wasting any space.

I can see how it might cause a problem for a backup routine that is not configured not to recurse into symlinked directories as it is going to recurse into that X11 symlink ad infinitum.

---

