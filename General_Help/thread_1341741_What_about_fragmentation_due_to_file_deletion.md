---
title: "What about fragmentation due to file deletion?"
date: 2009-11-30
forum: General Help
---

### Post by Cytochromec on 2009-11-30
So I read the popular [link]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") explaining why I dont need to defrag my hard drive using ext4 over, say, NTFS. I also heard people mention going years without defragmentation. What about fragmentation caused by deleting files? The link explains how files can grow and be moved avoiding fragmentation, but it doesnt say anything about crumbs left over after the cookie is gone. In which case, I would wonder again, about defragging my drive. Also, how in the world can I trust online defragmentation for ext4? Thanks.

---

### Post by earthpigg on 2009-11-30
in MS Windows X, running NTFS? defrag more than once a year is almost always excessive. in fact, defragging to much ***contributes*** to fragmentation. true story.

unless you are running an enterprise-class database, do not worry about it.

unless your hard drive is over 85% full, do not worry about it unless you have not done a fresh install in a decade.




and if none of that is the case? here is how we defrag....

form an archive of your data. save it elsewhere. delete the data. restore it from your archive.

there, it is defragmented.

do not bother worrying about it more than once a decade. seriously.

---

### Post by Cytochromec on 2009-11-30
> **earthpigg said:**
> 

and if none of that is the case? here is how we defrag....

form an archive of your data. save it elsewhere. delete the data. restore it from your archive.

there, it is defragmented.

do not bother worrying about it more than once a decade. seriously.

Hehe, I actually do that from time to time and a format is basically the same thing for the OS partition on my drive. I been defragging for a long time now and I think it, along with windows, is a thing of the past for me. It was just one more thing to do. I dunno, maybe I liked seeing the colourful analyses defrag progies have, but its felt pointless for quite some time. You just dont see any noticeable difference and that in itself is enough bench testing for me I guess. Alas, its something to tell future children about. 

Gonna miss some of that sweet placebo though...I could always use more placebo...

---

### Post by Agent ME on 2009-11-30
> **Cytochromec said:**
> So I read the popular [link]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") explaining why I dont need to defrag my hard drive using ext4 over, say, NTFS. I also heard people mention going years without defragmentation. What about fragmentation caused by deleting files? The link explains how files can grow and be moved avoiding fragmentation, but it doesnt say anything about crumbs left over after the cookie is gone.
What crumbs would a deleted file leave? When a file is deleted, the space used by it is then free to be used by other files. The system doesn't try to avoid writing on the remnants of the deleted file.

---

### Post by Cytochromec on 2009-11-30
> **Agent ME said:**
> What crumbs would a deleted file leave? When a file is deleted, the space used by it is then free to be used by other files. The system doesn't try to avoid writing on the remnants of the deleted file.

So if I have a 1000 tiny 1MB files located together on the disc and delete all of them at once, does that equate to remove one large 1GB file?

---

### Post by madverb on 2009-11-30
> **earthpigg said:**
> in MS Windows X, running NTFS? defrag more than once a year is almost always excessive. in fact, defragging to much ***contributes*** to fragmentation. true story.

unless you are running an enterprise-class database, do not worry about it.

unless your hard drive is over 85% full, do not worry about it unless you have not done a fresh install in a decade.

and if none of that is the case? here is how we defrag....

form an archive of your data. save it elsewhere. delete the data. restore it from your archive.

there, it is defragmented.

do not bother worrying about it more than once a decade. seriously.

That is misinformation. Defrag as often as you like.

---

### Post by John Bean on 2009-11-30
> **Cytochromec said:**
> So if I have a 1000 tiny 1MB files located together on the disc and delete all of them at once, does that equate to remove one large 1GB file?
For the purpose of reusing the space? Yes. 1000 1MB files probably isn't !GB of disk space though ;-)

---

### Post by SeanBlader on 2009-11-30
Defrag is a con perpetrated by utility software makers because of people who use out-dated hardware to run poorly written software. If you use that same hardware for well written software, all of a sudden you find that performance isn't lacking after a few years of running the same install.

Conveniently enough, if you run a well partitioned Ubuntu setup, you will get new OS versions before your drive has a chance to become fragmented.

Unfortunately though if you're running an 8 year old operating system with thousands of updates on 8 year old hardware, you probably have bigger problems than defragmenting your hard drive. You're probably lucky that it still boots since you're likely way past the MTBF (Mean Time Before Failure).

---

### Post by mixmaster on 2009-11-30
Fragmentation becomes a problem when you have large files scattered in small pieces all over the disk platter(s).  If you then have to do a sequential read of the whole (or a significant part) of the file your performance can be adversely affected.  Generally this is only a problem with applications - large sequential data reads are fairly rare except for streaming media where other bottlenecks will generally outweigh any issues with disk read performance.

Since any half way competent file system will put a file in a sequential set of sectors if it possibly can you are only likely to get significant fragmentation when your disk is pretty full and you are constantly deleting and writing program files.  Even then your usage pattern has to be pretty pathological for it to become a noticable issue.

---

### Post by madverb on 2009-11-30
Wow, now there is conspiracy theories about defragmentation... AWESOME!

---

