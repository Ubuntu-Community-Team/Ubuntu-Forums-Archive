---
title: "Corrupt tar gz file -- any chance to recover data?"
date: 2012-09-30
forum: General Help
---

### Post by muet0005 on 2012-09-30
Hello,

I've been trying to extract data from a tar gz file, however all of my attempts are getting stuck at a particular location in the file.

I created a the file as a backup a few months back using "tar zcfv", and have checked using "file" that it is in fact a  tar gz file.

I've tried the following to extract the data:

tar zxfv 

cpio -ivd

and 

gzrecover

Both exit (tar with this message:   tar: Exiting with failure status due to previous errors  , and gzrecover with a segmentation fault).  I also was able to get a "corrupt file" error, I think from tar or cpio, at some point (perhaps on my mac, but not on ubuntu).  The tgz file is about 60GB, so it's quite large.  All of these data were backup on two separate external hard drives, but unfortunately the computer and both external hard drives were stolen after someone broke into friends house.  I happened to have backup her external hard drive (before formatting it for her) in multiple locations,  one happened to be this tgz file, which I was able to recover from a time-machine backup.

so, The main issue here is, tar, gzrecover and cpio all fail when recovering the file.  I can get to about 11GB of data out of this 60GB tar gz file before these programs fail...


Does anyone have any advice on how to get more data from this tar file?  Is there a way to prevent the segmentation fault from gzrecover or to force tar or cpio to keep going after it hits the corrupted part of the file?


Any advice would be greatly appreciated.  I'm willing to spend time on this, as my friend lost all of her data from that theft...

---

### Post by cbraxton on 2012-09-30
If you do a web search on "recover data corrupt tar file" you'll find quite a bit.

Can you at least gunzip it without errors? You'll probably have a better chance at recovery if the tar file is not compressed. If you get gunzip errors you can try this:

[http://www.gzip.org/recover.txt](http://www.gzip.org/recover.txt)

...or this:

[http://www.urbanophile.com/arenn/hacking/gzrt/gzrt.html](http://www.urbanophile.com/arenn/hacking/gzrt/gzrt.html)

There is a commercial program called "Advanted Tar Repair" that runs on Windows and claims to be able to repair tar files. It costs $150(US) but has a money-back guarantee. If the data is valuable and you have access to a Windows system it might be worth a try:

[http://www.datanumen.com/atr/](http://www.datanumen.com/atr/)

(I am not affiliated with that company and have not tried their product myself.)

---

### Post by muet0005 on 2012-09-30
Thanks, cbraxton...this is helpful.

The google search you mentioned is exactly what I've done, and have tried a number of the suggestions.

I did also try advanced tar repair on a windows computer, and it did in fact fail.

I have tried to gunzip the file first...and that fails a few gigs into the file....but, I haven't tried the gzip recovery you mentioned (I think this is different from gzrecover, which is part of the gzrt package).  So, I will give that a whirl...perhaps if the gzip recovery can extract a valid tar archive, I'll be in business.


I am currently trying out "SysInfoTools Archive recovery" in windows...this thing has been running for a day now, but it did get past the corrupt block in the tar archive...so I'm waiting to see the result of that as well...

Thanks again for the suggestions...

-Ryan

---

