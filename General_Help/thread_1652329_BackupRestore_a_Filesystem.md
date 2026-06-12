---
title: "Backup/Restore a Filesystem"
date: 2010-12-24
forum: General Help
---

### Post by seandude on 2010-12-24
I've been thinking of trying out a few new distros, but I would like to do a complete system backup before I do.  I've been reading about the options, but am a bit confused about the different options/techniques.  I'd rather actually understand what I'm doing before taking the plunge so there are two parts to this: technical questions that are just about how different things work, and questions specific to my personal backup.  Any information would be helpful.

1. What is the difference between using a program like Clonezilla and just going `[FONT="Courier New"]cat / > /mnt/Foo[/FONT]`?

2. What is the difference between using [FONT="Courier New"]dd [/FONT], [FONT="Courier New"]tar [/FONT] and [FONT="Courier New"]cp -a[/FONT]?

3. One article I read [here]("http://www.halfgaar.net/backing-up-unix") warns against storing ownership textually, and suggests that you use numerical storage.  How exactly is that information stored textually or numerically?

4. That same [article]("http://www.halfgaar.net/backing-up-unix") also warns against losing hard links by using cp -a.  How exactly does this work?


Now, what I'm planning on doing is backing up my entire hard drive (136 GB used, ext4, mounted on [FONT="Courier New"]/dev/sda1[/FONT]) onto a 500 GB external hard drive.  I don't dual boot, so I've only got one partition.  I only have 76 GB of unused space, so I'd prefer to just write directly to the external hdd, and I'd rather do it while my system is live and not running off a bootable cd.  I don't really care how long the process would take, reliability and keeping my data's integrity is most important to me.  

Ideally, should I end up being unhappy with any of the distros I try out, I'd be able to just plug my external hdd into the laptop, and overwrite the file system.

This is what I've read, please tell me if there's faulty information on any of the pages.

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)
[http://www.halfgaar.net/backing-up-unix](http://www.halfgaar.net/backing-up-unix)
[http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation](http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation)

---

### Post by noah++ on 2010-12-24
> **seandude said:**
> 1. What is the difference between using a program like Clonezilla and just going `[FONT=Courier New]cat / > /mnt/Foo[/FONT]`?
You'll find that [FONT=Courier New]cat[/FONT]ing a directory like [FONT=Courier New]/[/FONT] won't do anything. But [FONT=Courier New]cat[/FONT]ing a device like [FONT=Courier New]/dev/sda[/FONT] with your syntax can make a block-level copy of it, much like [FONT=Courier New]dd[/FONT]. It's just that [FONT=Courier New]dd[/FONT] has options for block size and other stuff.

> 2. What is the difference between using [FONT=Courier New]dd[/FONT], [FONT=Courier New]tar [/FONT] and [FONT=Courier New]cp -a[/FONT]?Like I said, [FONT=Courier New]dd[/FONT] makes a block-level copy of a device. So it duplicates any structures above the block level perfectly -- partitions (one or more), filesystems and boot sectors. When it's time to restore a disk, those partitions and filesystems and the boot loader are restored all at once. There are other block-level copy programs out there, and [FONT=Courier New]dd [/FONT]is one of the ones Clonezilla uses (the slowest one, in fact).

[FONT=Courier New]tar[/FONT] and [FONT=Courier New]cp[/FONT] provide filesystem-level backups. If you want to back up or restore your partition table or bootloader, they can't easily help you. And, to make a perfect copy, they also have to be aware of all the extended attributes of your source filesystem(s). That's hard to verify. If you use a stock Ubuntu distro, though, I don't think it'll matter.

In the case of [FONT=Courier New]cp[/FONT], your target filesystem(s) ought to be the same as your source one(s). A source filesystem may use attributes the target doesn't use or doesn't understand. They may support differing character sets. The same data can also occupy more or less disk space in different filesystems; in the case of sparse files, the difference can be radical.

Hopefully all this is helpful, and equips you to answer your other questions.

---

