---
title: "Advice on creating partitions for data"
date: 2010-05-19
forum: General Help
---

### Post by poetofcode on 2010-05-19
So, I guess I must have OCD. I want to reorganise all my data onto my 1TB Western Digital MyBook drive.

I've got the segmentation I'd like down to this simple model:

**Storage** - which comprises a general file dump, my home partition, and a partition for backups;
**Installations** - where I want to host my root partitions for my Linux distributions, and also a partition to dump a bunch of Windows apps on, a la Portable Firefox;
**Multimedia** - one partition holding my music, movies and photos.

So, I only really have a general idea of the way the world of disk partitioning works. I'm sure a partition can't *contain* another, but this effect is achieved in Linux distributions that separate the /home directory from the / partition.

My guess is, that to achieve the following structure on my drive, I would initially need to create an all-containing partition which contains nothing but directory structure and mount points.

Second, I need to create my partitions for home, backups, linux root, windows apps, linux apps (/opt) and multimedia.

Finally, to achieve the effect of one megalithic massive file system containing my entire digital life on one portable hard drive, I simply edit my /etc/fstab to reflect where my partitions appear.

This is the structure I'm going for. Please feel free to advise me how to go about it - and if it's not really feasible, please break the news gently. :) Organisation on this level is truly beautiful, and it would be a shame if it were not possible.

I've underlined the mount points where I'd have a partition mounted.

**All-containing partition**
[INDENT]- Storage[/INDENT]
[INDENT][INDENT]_Personal Settings_ (home partition, just used for dot-files to keep settings and personal file dump separate)[/INDENT][/INDENT]
[INDENT][INDENT]_Personal Files_ (documents partition, shared with other OS)[/INDENT][/INDENT]
[INDENT][INDENT]_Backups_[/INDENT][/INDENT]
[INDENT]- Installations[/INDENT]
[INDENT][INDENT]- Operating Systems[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- Linux[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]_Ubuntu Lucid_ (root partition for Lucid)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]_Crunchbang_ (root partition for #!)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT]- Installed Software[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- Linux[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]_Ubuntu Lucid_ (/opt for Lucid; kind of redundant because Debian-based distributions don't really use /opt - but certain packages do, like Grooveshark)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]_Crunchbang_ (/opt for #!)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- Windows[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]_Windows XP_ (Just a place to mount an NTFS partition, for installing apps the Portable Firefox way)[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT]_Multimedia_ - all music, movies and photos to be contained in this one partition.[/INDENT]

All help, advice and articles to read appreciated! :)

---

### Post by srs5694 on 2010-05-19
Your basic view is correct; however, be aware that creating too many partitions just makes your system inflexible. Consider: You create partitions, /foo/X and /foo/Y, of 2GB and 20GB, respectively, because you estimate you'll want to put twice as much data in /foo/Y as in /foo/X. Three months from now, however, you discover some reason to put lots of data in /foo/X, while /foo/Y no longer needs as much space. If you'd just created a single /foo partition of 22GB from the start, this problem wouldn't exist.

That said, splitting /home off from root (/) usually makes sense, and if you've got multiple OSes or Linux distributions, they usually each require their own partitions. Advanced users often split off some others, such as /usr, /opt, /var, or even /tmp.

I wrote [an introductory piece on partitioning](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) for IBM developerWorks a while back. You may also want to check out the [Filesystem Hierarchy Standard (FHS) documentation;](http://www.pathname.com/fhs/) the FHS is the standards document that describes where stuff goes in a Linux system.

---

