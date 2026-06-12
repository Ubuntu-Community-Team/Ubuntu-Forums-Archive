---
title: "best format for USB HD for rsync-based archiving?"
date: 2010-11-30
forum: General Help
---

### Post by tlroche on 2010-11-30
**summary:** I just got a FAT USB HD for backup/restore. I'm wondering, should I reformat to ext[234], and if so, which one?

**details:**

I archive using rsync and duplicity mostly to/from lucid boxes, e.g.

> $ lsb_release -ds
Ubuntu 10.04.1 LTS
$ uname -rv
2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:58:05 UTC 2010

Having filled my previous archive target I got a new HD that's USB, external, electromechanical (not SSD), and of course FAT:

> $ sudo lshw -C disk
...
> *-disk
>      description: SCSI Disk
>      physical id: 0.0.0
>      bus info: scsi@21:0.0.0
>      logical name: /dev/sdb
>      size: 596GiB (640GB)
>      capabilities: partitioned partitioned:dos
>      configuration: signature=24796452

When archiving I value, in approximately descending order of importance,

[LIST=1]
[*]Reliability. I.e. when I backup a file to the archive, I expect to be able to restore it.
[*]Speed. Backup is not fun, and slow backups degrade discipline.
[*]Interoperability. While I will normally only backup to and restore from approx the same kernel versions (and therefore to/from linuxen), I'd like to be able to restore to, e.g., XP or 7 or OSX. That being said, I will cheerfully sacrifice interop to improve reliability and speed.
[/LIST]

I'm wondering, which of {ext2, ext3, ext4} is most appropriate for this usecase? Or will FAT provide as much reliability and performance as any of ext[234] in this usecase, e.g. connecting via USB? (I'm assuming FAT is more interoperable--please correct if wrong.)

Apologies if this is a FAQ (though I didn't see anything like it in the [ext4 FAQ]("https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions"), or searching this forum, or just googling). If I should RTFM, please point me to something targeting filesystem users, not FS developers.

TIA, Tom Roche [Tom_Roche@pobox.com]

---

### Post by oldfred on 2010-11-30
I cannot recommend FAT for anything except those devices that have to have it like your camera, phone, or xbox. File size limit of 4GB and no journal. 

If you are working with windows you need NTFS. But if you copy Linux data to NTFS then you lose permissions & ownership and have to reset those on recover.

I am using ext4 just because the fsck runs so much faster. I do not think you want ext2 as that is not journaled, but discussions remain on ext3 or ext4 on speed & reliability. Ext4 originally was much faster, but had reliability issues. In fixing the reliability issues it become only a little faster on many things, but fsck is still a lot faster.

---

### Post by AlphaLexman on 2010-11-30
@ oldfred -> +1

I have an external hard drive for backups and audio.
Two partitions, audio is ext4 and backups is ext3.
I went with ext3 for the backups for the reliability.
Although that was a year ago, and ext4 is better now.

---

