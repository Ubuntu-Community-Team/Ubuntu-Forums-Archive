---
title: "Good or bad: 16% of my files are non-contiguous"
date: 2006-06-26
forum: General Help
---

### Post by jongkind on 2006-06-26
I question the claim that file defragmentation in Linux is not relevant. I hope that you can clarify this. Details are given below. 

**Details**
It is claimed that one of the advantages of Linux is that file defragmentation does not happen or occurs only at a very low level. However, after 3 months of using my newly installed home partition fsck indicates that 16% of the files of my home are non-contiguous. This makes 64% when I extrapolate this to 1 year. 

This does not seem worse or better to me than what happens with file fragmentation in Windows XP. This latter OS has a defragmentation utility though. 

This concerns me a bit. One possibility to reduce the defragmentation is to copy the files of my home partition to another partition followed by copying them back again. This is, however, a cumbersome process.

In summary, I question the validity of the claim that file defragmentation in Linux is not relevant. Or do I overlook something?

---

### Post by aysiu on 2006-06-26
By that logic, in 18 months, your partition would be 100% non-contiguous, which is not possible.

First of all, you're assuming that fragmentation continues on a straight curve.

You also assume that 16% of your files being non-contiguous means that 16% of your files are bits and bytes scattered separate from one another. Perhaps you have a huge chunk of data, one empty block of data, and then the rest of your 16%?

I don't think you can conclude very much from having run *fsck* once after three months.

---

### Post by rai4shu2 on 2006-06-26
[QUOTE=jongkind]In summary, I question the validity of the claim that file defragmentation in Linux is not relevant. Or do I overlook something?[/QUOTE]

Yes, you did. You assumed that fragmentation is the product of time. Fragmentation is the result of several non-linear factors (including file size and the amount of free space). Non-linear results tend to bifurcate over time, not necessarily increase in a strict linear fashion.

---

### Post by jongkind on 2006-06-26
Thanks for your feedback. Yes, I agree on your points about extrapolation and the non liniarity. 

Nevertheless, I still don't know whether there is a real difference with XP. Can somebody illustrate this by some facts which would support the claim that Linux indeed is less sensitive towards file fragmentation?

---

### Post by aysiu on 2006-06-26
What kind of "illustration" would be proof enough for you? What kind of evidence are you looking for?

This may give you a better understanding of how it works:
[http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html)

You may want to look at this as well:
[http://wiki.arslinux.com/About_Defragmentation](http://wiki.arslinux.com/About_Defragmentation)

---

### Post by jongkind on 2006-06-26
Aysiu, thanks for this nice links. Although I was already aware of the philosophy behind it, it indeed indicates why Linux file systems would be less sensitive towards file fragmentation. It also indicates that it is unlikely that with Linux a file fragmentation of higher than 5% is reached. Well, with the 16% non-contiguous files of my home partition I ran into that situation already after 3 months of use (although the root is only 2% fragmented).

It maybe that this is typical for a home partition, which is heavily used by nature. On the other hand, there is still  75% of free space on that partition and the disk is also performing well according to S.M.A.R.T. So what is happening here?

I wonder, do you use a separate home partition, and if so, what results give fsck in terms of non-contiguous files?

---

### Post by aysiu on 2006-06-26
[QUOTE=jongkind]
I wonder, do you use a separate home partition, and if so, what results give fsck in terms of non-contiguous files?[/QUOTE] I don't have a separate /home partition, but I do have a separate data partition where I keep my music, pictures, etc. It doesn't appear to have any non-contiguous files: ```
username@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             8.8G  3.2G  5.2G  39% /
varrun                221M   92K  221M   1% /var/run
varlock               221M  4.0K  221M   1% /var/lock
udev                  221M  140K  221M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   19M  202M   9% /lib/modules/2.6.15-25-386/volatile
/dev/hda5             123G   48G   70G  41% /documents
username@ubuntu:~$ sudo umount /documents
Password:
username@ubuntu:~$ sudo fsck /dev/hda5
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/home: clean, 52156/16334848 files, 13090377/32658129 blocks
username@ubuntu:~$
```

---

### Post by padre999 on 2006-06-26
Quoting from

[http://os.newsforge.com/article.pl?sid=03/10/07/2028234&tid=2&tid=16&tid=31](http://os.newsforge.com/article.pl?sid=03/10/07/2028234&tid=2&tid=16&tid=31)

> As a general rule, fragmentation becomes a problem only if your disk is almost full. On a nearly full disk, Linux may have trouble locating a large enough block of free space to fit a file without fragmenting it. If you almost fill a disk and then delete files, the remaining files may or may not be fragmented, depending on which ones you deleted. For this reason, keeping your partitions from filling up is best. As a general rule, anything less than 80 to 90 percent full is fine from a fragmentation perspective.


and from

[http://www.salmar.com/pipermail/wftl-lug/2002-March/000603.html](http://www.salmar.com/pipermail/wftl-lug/2002-March/000603.html)

> The performance difference between a
'file fragmented' Linux file system and a 'file unfragmented' Linux
file system is minimal to none, where the same performance difference
under MSDOS would be huge. 

and from [http://www.linux.org/docs/ldp/howto/Partition/appendix.html](http://www.linux.org/docs/ldp/howto/Partition/appendix.html)

> DOS users are accustomed to defragging their disks every few weeks and some have even developed some ritualistic beliefs regarding defragmentation. None of these habits should be carried over to Linux and ext2. Linux native file systems do not need defragmentation under normal use and this includes any condition with at least 5% of free space on a disk.

---

### Post by jongkind on 2006-06-26
Thank you all for your help. I'll let it go for the moment, although it is a bit irritatitating that fsck indicates a 16% /home partition fragmentation.  Nevertheless, I don't observe a performance loss, so who bothers?  

Hm :neutral: .

---

### Post by ReapeX on 2007-01-19
From a 2 month ubuntu user:

Thanks for the thread, I was about to "bother," because ubuntu is reporting my file system is 0.5% fragmented.  I know that is basically nothing, however when I login to Ubuntu today I was unable to go to any sites even though I had an ip address from my ISP.  Then I tried running programs from the system menu but none of the applications would load.  I guess, it could have been a resource causing some type of deadlock situation (system monitoring tool wouldn't run).  

I restarted Ubuntu and everything worked fine, however I am still receiving the 0.5% non-contiguous problem (now I believe it's 1.5%).  Hmm, I'll probably read the links that were posted on this thread.  

Thanks again for posting it,

ReapeX

---

### Post by psterrett on 2007-10-21
I don't care what you cypto-religious 'nix zealots say. I want my hard drive defragmented and compacted so that all the free space is at the end. "Less sensitive to framentation" doesn't mean zero fragmentation.

---

### Post by jongkind on 2007-10-21
> **psterrett said:**
> "Less sensitive to framentation" doesn't mean zero fragmentation.

You're very right! 

And via the link you have access to pyfragtools, which is an very efficient defragmenter. I use it at 1 laptop and 4 desktop PC's. Especially the /home partitions of these computers are sensitive towards fragmentation. After running pyfragtools on these partitions the level of fragmentation is < 1 %. After 1-2 months of use this is in the 8+ % regime again.

Pyfragtools:
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

---

### Post by jaybombalous on 2007-11-01
> I want my hard drive defragmented and c**ompacted so that all the free space is at the end**


if you read pyfragtools u will notice that it does not compact and allocate free space at the end, instead it just defragments the files. Read the threads people and stop spreading untruths.

Don't take my word for it, take the word of the guy who programmed it.

---

### Post by thx11381974 on 2007-11-01
> **psterrett said:**
> I don't care what you cypto-religious 'nix zealots say. I want my hard drive defragmented and compacted so that all the free space is at the end. "Less sensitive to framentation" doesn't mean zero fragmentation.

My understanding is Linux doesn't store data the same as M$ compacting so all free space was at the end would make the drive work worse not better.

This link gives a good explanation

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by LaRoza on 2007-11-01
> **psterrett said:**
> I don't care what you cypto-religious 'nix zealots say. I want my hard drive defragmented and compacted so that all the free space is at the end.

End? There are no "ends" of a series of circular platters. 

Most Linux file systems do not compact like you seem to want, because it causes fragmentation, and besides, EXT3, which you are probably using, is a journalling file system.

---

### Post by psusi on 2007-11-05
Aysiu, you did not perform a fsck on your drive; it just saw that the volume was clean and quit without doing anything.  You need to fsck -f to force it to run.  

LaRozza, journaling hasn't got a thing to do with fragmentation.  

Even having 15% of your files non contigous is not a problem.  If you have a lot of 600 MB movile files for instance, they are almost certainly going to not be fully contiguous, but having it be in 3 x 200mb chunks is not a problem.  Fragmentation is a problem on windows because it tends to take a 50 MB file and split it into 150 fragments.  

If you are really paranoid you can boot from the livecd and install the defrag package and run e2defrag on your ext3 partition.  It will fully defragment all files, optimize directories, and pack files to coalesce free space.

---

### Post by deepclutch on 2007-12-10
btw,dont run fsck on a mounted partition! :p

---

