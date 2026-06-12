---
title: "How can I dump raw contents of a HDD into a single file?"
date: 2006-02-21
forum: General Help
---

### Post by branco on 2006-02-21
Actually, I need to check out the contents of a {rm -r}'d HDD (60Gb total) that I whined about a couple of days ago, so if you have a better idea, please tell me.

I've heard about the "dd" command, but it would only create an exact copy of the hard drive on another hard drive, right? How about "grep"? I've heard about it before. Can it do the job, or is it text-data only? I need a file I can feed to the data carving apps. I intend to dump the contents into a file, and then remove the HDD physically in order to prevent overwriting data.

Of course, I am aware of boot CDs like Knoppix STD and Helix which wont even touch the HDD, but I was kind of wondering if I can use what I feel confortable with -- the Ubuntu Linux, and, of course, keep the system I've benn painstakingly tailoring to my needs for six months+.

---

### Post by z_diver on 2006-02-21
I would think dd is the command that most closely does what you what you asked.  dd is incredibly flexible and you can probably have the results tarred to save the permissions and have everything in one file.  I had an "issue" like this once.  Here are some notes i wrote down afterwards which helped me get about 300 files out of a total 700.

1)  First I ran 'sudo debugfs /dev/hdb2' and once into debug mode ran
'lsdel'.  This brought up a long list of files in chronological order that
I could possibly recover.  PgDn to the bottom and only 2 files were recent
so I dumped that data to files in my /tmp directory. The syntax was 'dump
<some-inode#> /tmp/recovered1. which gave me a pdf. Good, got one back out
of two that looked recent so 50% recovery rate there.

Next I got further into the Ext3 recovery processes using this link as a
guide.  [http://linux.sys-con.com/read/117909_1.htm](http://linux.sys-con.com/read/117909_1.htm) There they describe
some of the methods you can employ for recovery and go through the basics
of the Ext3 file system.  Good read even if you don't need it just yet.
Using these methods I was able to see exactly what was deleted and got
back most of what I couldn't get from my backups.  And had I not, even
just knowing what was deleted would have been a big help.

Btw, it seems most of the utilities available(recover, gtkrecover,
formost, TSK, and Autopsy) are available from the Ubuntu repositories. One
heck of an impressive looking utility is Autopsy.  It might be a little
much if you just need it for one job as it starts it's own local webserver
which you use for filing a "case" and looking after that case.  I had
already recovered most of what I needed before I found Autopsy but it
seems like it would be a good starting point next time(supposing there is
a next time).

For what it's worth I thought I'd post my experiences here because so much
of what you read on the net says file recovery on ext3 just can't be done.
It seems it can be, but isn't anywhere near as automatic as one would hope
for and it likely won't be 100%.

---

### Post by az on 2006-02-21
That was very informative!  I didn't realise that foremost was in the repositories....  I am going to clobber a hard drive just to be able to play around with autopsy!



As for imaging your drive, dd is the way to go.  If you have another drive (or a partition) that is big enough to handle the 60 gigs, you should make an image of the drive and work on recovering the lost files from that image, so that you can always start over if your bork it.


dd if=/dev/hda1 of=file
where you are creating the "file" file in a directory with enough free space.

---

### Post by Fred Doolie on 2006-02-21
> dd if=/dev/hda1 of=file

Is that the way to backup an entire partiton somewhere? Will that save everything; MBR, partiton table and all?

Most importantly, can the image be restored onto a larger partition? Sounds like Linux pretty much has "Ghost*" build into it!

EDIT: Answers were found to be yes to saving everything and no to the larger drive. The drive must be 100% the same type and size.
So the question is how can I image my Ubuntu and put it onto a larger partition? It looks like partimage won't do that either. If this were Winblows I could use Ghost but Ghost won't work on Ext3 partitions. There must be some Linux equal to Ghost. I just want to image the partition, redo my HDA to a larger setup and then put it all back without losing anything.

---

### Post by branco on 2006-02-23
Thanks, you all, for helping me out with this. I finally decided I could NOT keep ubuntu, because I had to wipe the HDD ubuntu was on to free up just about enough space for the image file.
So I got the Recovery Is Possible (R.I.P.) boot CD which has a preinstalled foremost and weighs at 30MB (for a quick download). 'dd' worked like a dream and my image was completed in about 45 minutes. Then I fed the image to foremost, and it 'recovered' some 90000+ pics (wtf?!). I guess it found some false jpgs in there. I will preview the pics later and see if all the files are there.
BTW, I think R.I.P. is a great CD. I tried KANOTIX, Penguin Sleuth, Helix... KANOTIX is just a Live distribution and hasn't got 'foremost', Penguin Sleuth uses an ancient kernel and is a bit too slow on my PC. Helix is the worst of all (it's supposed to be a forensics-optimized live distro). It's bloated with memory-sucking apps that fail miserably in the end, and 'dd' ran for 5 heroic hours before I killed it.
Thanks again!

---

