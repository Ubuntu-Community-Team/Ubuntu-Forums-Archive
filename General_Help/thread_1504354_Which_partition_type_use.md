---
title: "Which partition type use"
date: 2010-06-07
forum: General Help
---

### Post by inmortal009 on 2010-06-07
Hi a new Ubuntu user is here :) well...I was reading about Why Windows need defragmentation and why Linux not.I made a dual boot W7 and Ubuntu installed with Wubi, therefore my 25gb Ubuntu partition is NTFS has you can see here

[http://img580.imageshack.us/img580/1356/screenshotsi.png](http://img580.imageshack.us/img580/1356/screenshotsi.png)

If I leave that format my Ubuntu will run inefficient and I gonna need defragment? Can anyone advice me about which format use and why please...

thanks in advance...sorry for my english ):P

---

### Post by inmortal009 on 2010-06-08
???

---

### Post by darolu on 2010-06-08
Well, first keep in my mind I have never installed Ubuntu via Wubi, with that said this is what I *know*: I have heard and read that Wubi installs in a virtual drive, this is a file that reserves space, basically like a Virtual machine, so you won't be able to change the *filesystem* (in your words *partition type*) to something different than NTFS.

I personally see Wubi installations more like a safe-test than an actual installation, so if you liked it, you should install (the real way) it, partitioning your hard drive to your likings.

The default **Ext4** filesystem is appropriate for most users, it is stable, is fast, allows you to move large files and as you have already found, no defragmentation issues. It would be my recommendation.

Another good option is XFS.

---

### Post by yetiman64 on 2010-06-08
> **darolu said:**
> ... this is what I *know*: I have heard and read that Wubi installs in a virtual drive, this is a file that reserves space, basically like a Virtual machine, so you won't be able to change the *filesystem* (in your words *partition type*) to something different than NTFS....


True, so to change you're partition type, you would have to consider uninstalling the wubi install in Windows (Check out the "Add/Remove Programs" or "Software and Features" --depends on your Windows version-- in Control Panel).

Then you would need to shrink the windows partition with a partitioning tool (it is recommended to defragment Windows first). Then install Ubuntu to the unallocated space from a live-cd. That is, do a full separate partition install. This would give you an ext4 partition type.

As you already have Ubuntu installed **inside of **Windows I'd suggest you not "worry" too much about the filesystem type and just defragment Windows as usual and use Ubuntu from there. **Just remember wubi is the installer that puts Ubuntu installed inside Windows **(and Ubuntu can be totally removed from there from Control Panel- just like a Windows Program.)

---

### Post by xjesse on 2010-06-08
You can't install Ubuntu on an NTFS partition. Go ext4 and you will be fine.

Remember you need:

/
/home
swap
/boot

no particular order.

Cheers.

---

### Post by Sef on 2010-06-08
> Remember you need:

/
/home
swap
/boot

A boot partition is not necessary.  Neither is a home partition, but it is nice to have.

---

### Post by sidzen on 2010-06-08
use ext4
/
/home
swap
per Slackware recommendations

---

### Post by yetiman64 on 2010-06-08
> You can't install Ubuntu on an NTFS partition...@xjesse, Ahhh, its called a "wubi" install :) , as the OP has already done! 

Check out the disk utility link the OP posted carefully for clarification as it's showing Ubuntu on an NTFS partition. It might be the case is the OP may be misunderstanding filesystem types and when and where they're used etc. Cheers yetiman64 :).

<off topic edit>
@sidzen,  :lolflag:'ed at the attached thumbnail. Thanks, needed that.

---

### Post by inmortal009 on 2010-06-08
Thank you for clarifying some doubts. I found that my file system in fact is ext4 just see the screenshot

[http://img535.imageshack.us/img535/5717/screenshot2pq.png](http://img535.imageshack.us/img535/5717/screenshot2pq.png)

However I'll delete it and install with a live cd  ):P

---

### Post by sidzen on 2010-06-09
You're welcome!  
What is that, a Maribou stork?

---

### Post by yetiman64 on 2010-06-09
<off topic>

> **sidzen said:**
> You're welcome!  
What is that, a Maribou stork?

An Ibis.
btw, I'm now using the pic as my destop :biggrin: (couldn't help myself). Cheers Yetiman64

<back on thread>

>               **Re: Which partition type use**
          Thank you for clarifying some doubts. You're welcome inmortal009 :). Cheers Yetiman64.

---

### Post by bodhi.zazen on 2010-06-09
> **inmortal009 said:**
> Hi a new Ubuntu user is here :) well...I was reading about Why Windows need defragmentation and why Linux not.I made a dual boot W7 and Ubuntu installed with Wubi, therefore my 25gb Ubuntu partition is NTFS has you can see here

[http://img580.imageshack.us/img580/1356/screenshotsi.png](http://img580.imageshack.us/img580/1356/screenshotsi.png)

If I leave that format my Ubuntu will run inefficient and I gonna need defragment? Can anyone advice me about which format use and why please...

thanks in advance...sorry for my english ):P

Well there are two issues :

1. Windows . Your wubi install is a file on yoru NTFS partition and as with all files on NTFS is subject to fragmentaion.

You can try using the various defragmentation tools on your NTFS drives and you may have varying degrees of success.

2. Linux. In general linux file systems do not suffer from **significant** fragmentation. Yes there will be some fragmentation. Often it is 1-2 % at the most and I have never seen a linux file system more then 5% fragmented. You probably need at least 25 % fragmentation to see any difference in performance, so it is almost a non-issue on linux.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Getting back to your issue, wubi is for giving Ubuntu a try. If you want to use it long term I suggest you do a standard installation, including deleting the wubi install, partitioning your Hard drive, and installing Ubuntu.

Maintaining a wubi install is much more complicated as it involves things such as loop mounting a file system within a file system, etc.

---

### Post by inmortal009 on 2010-06-09
1000 thx for help me with NTFS ect....specially @[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") I'll intall it with a CD :guitar:

---

### Post by sidzen on 2010-06-10
Your wrap-up clarified what *wubi* * is for me and your signature is a good reminder -- Thanks!


*obviously i don't use Windows

---

