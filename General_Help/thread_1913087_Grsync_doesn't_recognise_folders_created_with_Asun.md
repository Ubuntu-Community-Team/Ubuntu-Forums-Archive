---
title: "Grsync doesn't recognise folders created with Asunder"
date: 2012-01-21
forum: General Help
---

### Post by habana on 2012-01-21
I recently started using Asunder to rip CDs (R.I.P. Grip). When I try to backup my /home directory to a flash drive, the new folders created by Asunder are not recognized by Grsync. At first I thought it was an upper case/lower case or a 'space in filename' problem but it is not. If I Rename the folder typing in exactly what was there before, the folder syncs OK. If I replace say six letters of a seven letter folder name, it does not sync, I have to retype the entire folder name.

The permissions/owner of these folders are identical to those of the other folders which grsync recognizes. Banshee recognizes and plays all my recorded files.

Here is a typical error report if I try to rsync one such folder:

> *** Launching RSYNC command:
rsync -r -t -v --progress /home/bill/mp3/Skip James /media/CORSAIR/mp3/Skip James

sending incremental file list
rsync: link_stat "/home/bill/mp3/Skip James" failed: No such file or directory (2)

sent 12 bytes  received 12 bytes  48.00 bytes/sec
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
total size is 0  speedup is 0.00
Rsync process exit status: 23

After retyping:

> *** Launching RSYNC command:
rsync -r -t -v --progress /home/bill/mp3/Skip James /media/CORSAIR/mp3/Skip James

sending incremental file list
created directory /media/CORSAIR/mp3/Skip James
Skip James/
Skip James/ Today!/
Skip James/ Today!/All Night Long.mp3
     9711616 100%   28.58MB/s    0:00:00 (xfer#1, to-check=12/15)
Skip James/ Today!/Cherryball.mp3
     8603648 100%   15.75MB/s    0:00:00 (xfer#2, to-check=11/15)
Skip James/ Today!/Crow Jane.mp3
     5771264 100%    7.13MB/s    0:00:00 (xfer#3, to-check=10/15)
Skip James/ Today!/Cypress Grove.mp3
     8353792 100%    5.58MB/s    0:00:01 (xfer#4, to-check=9/15)
Skip James/ Today!/Drunken Spree.mp3
     5421056 100%    2.72MB/s    0:00:01 (xfer#5, to-check=8/15)
Skip James/ Today!/Hard Times Killing Floor Blues.mp3
     6547456 100%   13.46MB/s    0:00:00 (xfer#6, to-check=7/15)
Skip James/ Today!/How Long.mp3
     5701632 100%    4.18MB/s    0:00:01 (xfer#7, to-check=6/15)
Skip James/ Today!/I'm So Glad.mp3
     3667968 100%    5.78MB/s    0:00:00 (xfer#8, to-check=5/15)
Skip James/ Today!/Look Down the Road.mp3
     6289408 100%    4.88MB/s    0:00:01 (xfer#9, to-check=4/15)
Skip James/ Today!/My Gal.mp3
    11728896 100%   12.80MB/s    0:00:00 (xfer#10, to-check=3/15)
Skip James/ Today!/Skip James - Today!.mp3.m3u
         752 100%    0.83kB/s    0:00:00 (xfer#11, to-check=2/15)
Skip James/ Today!/Special Rider Blues.mp3
     9979904 100%    4.47MB/s    0:00:02 (xfer#12, to-check=1/15)
Skip James/ Today!/Washington DC Hospital Center Blues.mp3
     8079366 100%    6.55MB/s    0:00:01 (xfer#13, to-check=0/15)

sent 89868721 bytes  received 267 bytes  8558951.24 bytes/sec
total size is 89856758  speedup is 1.00
Rsync process exit status: 0

No doubt this is something simple but any help appreciated.

Ubuntu 11.10

---

### Post by habana on 2012-01-23
Bump

---

### Post by ta33ers on 2012-06-25
Asunder is creating file names with spaces, these can be accesed from a gooie but not from the command line. I tried to change this in the preferences but had no success. If someone has a solution it would be welcomed. Thanx

---

### Post by HiImTye on 2012-06-26
if you try to use rsync from the CLI do they work? i.e.

```
rsync -Prtv /home/bill/mp3/"Skip James" /media/CORSAIR/mp3/"Skip James"
```

---

### Post by habana on 2012-06-26
I did resolve this but it's five months ago and I've forgotten what I did:p

 I have a vague recollection that it was something to do with the character encoding of the CD information downloaded from the CDDB but how I fixed it I can't recall. It's certainly all working OK now.

---

### Post by richie60 on 2012-10-16
I have a similar problem with any folder created with asunder.  Do my rips, drag them over to an external drive to plug into my win7 media pc.  Windows reports an error along the lines of the folder not existing at the location!  However, i can open the folder and drag the files out but cannot drag the folder itself from the drive.

I have never come across this before because I can create folders in Ubuntu jist fine and they are seen in windows, but not with asumder.

---

### Post by dragonfly41 on 2012-10-16
I'm actually testing some grsync commands right now and my understanding is that an escape character "\" is required before spaces in the command line.  Is that relevant?

---

