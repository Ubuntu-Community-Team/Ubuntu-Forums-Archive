---
title: "gzip or tgz, what is better and/or what is standard"
date: 2009-07-10
forum: General Help
---

### Post by e24ohm on 2009-07-10
Folks,
I learning about gzip and tgz in school, but I am confused. Which service is better, and which service is standard, or more supported if there is such a thing.

Thank you.

---

### Post by t4thfavor on 2009-07-10
I think a tgz is just a gzipped tarball. tar is used to stick multiple files into one file, then gzip is used to compress them. For compression algorithms, I tend to like 7z, bzip, and gzip in that order. I believe that the latter two give better compression due to their more advanced algorithm but with this comes more overhead (CPU).

---

### Post by e24ohm on 2009-07-10
> **t4thfavor said:**
> I think a tgz is just a gzipped tarball. tar is used to stick multiple files into one file, then gzip is used to compress them. For compression algorithms, I tend to like 7z, bzip, and gzip in that order. I believe that the latter two give better compression due to their more advanced algorithm but with this comes more overhead (CPU).

Thank you for your help. I was confused because if I use the tar commands to compress i get "filename.tgz", but if I create the tar file, then use gzip i get "filename.tar.gz".

I was worried i was doing something wrong, or if there is a standard open source way to create compressed archive files.

thank you.
E

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi,

Ive just been reading a tutorial on backing up & restoring a full Ubuntu installation (mine, as I am about to resize my partitions 'on the fly')

It is excellent reading, simply put & explains about *.tgz  and *.tar.bz2

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

I last used unix (yeah, it was UNIX !!) over 20 years ago ... Have been having a gr8 time blowing off the cobwebs - odd thing is - the way these forums are structured - you actually learn WHY you do something, not just "This is what you do" :p

Enjoy learning, remember if you type in the search box at the top of the forums page - it will unlock a treasure trove of information, well written & understandable.

Regards,

Phill.


[/FONT][/SIZE]

---

### Post by e24ohm on 2009-07-10
> **phillw said:**
> [SIZE=2][FONT=Arial]Hi,

Ive just been reading a tutorial on backing up & restoring a full Ubuntu installation (mine, as I am about to resize my partitions 'on the fly')

It is excellent reading, simply put & explains about *.tgz  and *.tar.bz2

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

I last used unix (yeah, it was UNIX !!) over 20 years ago ... Have been having a gr8 time blowing off the cobwebs - odd thing is - the way these forums are structured - you actually learn WHY you do something, not just "This is what you do" :p

Enjoy learning, remember if you type in the search box at the top of the forums page - it will unlock a treasure trove of information, well written & understandable.

Regards,

Phill.


[/FONT][/SIZE]
thanks mate, that was a good read. Looking at trying to backup my system tonight, and try a restore.
cheers!!!

---

### Post by jerome1232 on 2009-07-10
.tgz is just short for .tar.gz just use whatever you prefer :)

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Once you have gotten your backup secure - the next 'fun' (Read as "scares the living day-lights out of me") thing to do is look at 'live' re-partioning.

Once I have my backup, I fear not. I'm shrinking the windows partion, shrinking the swap partion and enlarging the ext3 partion where Ubuntu lives. If nothing else, it'll be good for a laugh !!! :-)

Having read the forums, it seems suggested that the liveCD doesn't always have the latest version of GParted on it - this was somewhat unsettling to me, and may be 'old news'. 

Non the less, to be sure, to be sure... there is a link to get a bootable version of GParted in ISO format to make a CD with.

It is available from ...

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

As I find articles I am merrily book-marking them for future reference & the ability to pop them in as a reply to someone having a query I had when I 1st started with Ubuntu.

I've found this .....

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

If you want your brains blown out with knowledge ... this particular link is just plain scary !! - But, WOW, what a set of hints / tips, How to's etc....

[http://ubuntuforums.org/showthread.php?t=1166096&highlight=fstab+find+volumes](http://ubuntuforums.org/showthread.php?t=1166096&highlight=fstab+find+volumes)


Well, I will get my backup and re-partioning done !!!  I'm spoilt for choice !!!!

Regards,

Phill.

P.S. - And, that's linux for you ... start off on the difference between different tar-balls, and here we are - full system backups, restores etc ):P

[/FONT][/SIZE]

---

