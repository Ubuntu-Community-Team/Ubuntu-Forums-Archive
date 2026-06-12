---
title: "Which filesystem is the fastest?"
date: 2005-02-23
forum: General Help
---

### Post by Darrena on 2005-02-23
Looking around I see many people say Ext2 is the fasted, others say that Ext3 is now as fast as Ext2 and even others who say that Reiser is the fastest!

Right now I am running Ext3 but large file copies seem slow, does anyone know if the others are truly faster before I format some drives?

---

### Post by Yukonjack on 2005-02-23
If you are dealing with lots of files I mean lots Reiser is faster. For common usage I would have to say EXT3 is the norm.
I have used Reiser on a system that was used to move files around 1000+ and work really good for me. That was on a Libranet distro strip down using Fluxbox.

---

### Post by telmo on 2005-02-23
I saw a thread about this in fedoraforum. they had a link that showed that ext3 is really slow compared to xfs, reiserfs, etc...

But the fastest is xfs. I'm using it in Ubuntu Warty and it works really well. Of course you can't really say it's very fast compared to the others, because the difference is minimal. But it's faster.

---

### Post by alastair on 2005-02-23
[QUOTE=Darrena]Looking around I see many people say Ext2 is the fasted, others say that Ext3 is now as fast as Ext2 and even others who say that Reiser is the fastest!

Right now I am running Ext3 but large file copies seem slow, does anyone know if the others are truly faster before I format some drives?[/QUOTE]
 I suspect the filesystem will make little difference in average desktop use - be careful you are not going down a blind alley. Ext3 should be fine.

Try and be more specific about your problem - what hardware, disks, file size, kernel, command timed etc.

For a start, try "hdparm" to time you disk e.g.

hdparm -tT /dev/hda

Then perhaps move onto "dd" etc., check DMA and readahead as required.

---

### Post by Yukonjack on 2005-02-25
I knew I had a link about the file system, I just had to find it in my gazillion bookmarks. :)

[Fsbench](http://fsbench.netnation.com/)

---

### Post by bored2k on 2005-02-25
its good 2 remember its not only speed...

as long as its a Journalling file system , theyre all good ... a bad shutdown/crash on a non JFS will be as those old FPS games say ... "hurt me plenty"

---

### Post by ixus_123 on 2005-02-25
I use rieserfs just because it was the defualt on my last distro (slackware).  It feels bit faster than ext3 for my daily use but that could well be perceived & probably is.

The nail in the coffin for ext3 for me was hearing that it can't handle big files >2gb wich is no good for me & a lot of my video media files

---

### Post by Yukonjack on 2005-02-26
[QUOTE=bored2k]its good 2 remember its not only speed...

as long as its a Journalling file system , theyre all good ... a bad shutdown/crash on a non JFS will be as those old FPS games say ... "hurt me plenty"[/QUOTE]

Indeed.. priority is a good backup etiquette with those file system, laziness well suffer the.............   :cry:

---

### Post by bored2k on 2005-02-26
I found some interesting nFo sites for y'all .

id prefer RFS, its what ive been using for some time ... but i hav found some of the problems described on site # 1 ; ive been using ext3 ever since i installed ubuntu and so far so g0oD .

[Filesystem Guide](http://www-106.ibm.com/developerworks/linux/library/l-fs11.html?t=gr,lnxw16=FileSysP11) 

[Wich one is right for you?](http://www.linuxworld.com/story/32868_p.htm) 

[The Benchmark](http://linuxgazette.net/102/piszcz.html)

---

### Post by spiritraveller on 2005-02-27
[QUOTE=Darrena]Looking around I see many people say Ext2 is the fasted, others say that Ext3 is now as fast as Ext2 and even others who say that Reiser is the fastest!

Right now I am running Ext3 but large file copies seem slow, does anyone know if the others are truly faster before I format some drives?[/QUOTE]

Ext2 is only faster than ext3 because it doesn't do journaling.  Ext3 is just ext2 with some journaling features tacked on.  It's main advantage is compatiblity with the old standard.  If you're starting from scratch you can use whatever you want.

I'm trying out xfs right now, and it seems to be very good with playing movies.  It's strong point is supposed to be handling large files, so it makes sense.

I would go with Reiser, XFS or JFS... on the other hand, ext3 is more mature for what it's worth.

---

### Post by bored2k on 2005-02-27
[QUOTE=spiritraveller]
I would go with Reiser, XFS or JFS... on the other hand, ext3 is more mature for what it's worth.[/QUOTE]


not sure if we can do this on reiser or xfs , but  reading linux files on redmond is quite good [with ext2/3 partitions

---

### Post by alastair on 2005-02-27
# mount :

/dev/hda3 on /home type ext3 (rw)

# dd if=/dev/urandom of=/home/alastair/tmp/BIGFILE bs=1048576 count=3000
0+11 records in
0+11 records out
899 bytes transferred in 46.314714 seconds (19 bytes/sec)

# ls -l /home/alastair/tmp
-rw-r--r--  1 root     root     3145728000 2005-02-27 10:13 BIGFILE

Ext3 can handle > 2 GB - perhaps some applications have problems. But most audio stuff should be fine I would have thought.

---

