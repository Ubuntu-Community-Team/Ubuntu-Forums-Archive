---
title: "Trouble restoring from a compressed tarball"
date: 2011-11-15
forum: General Help
---

### Post by sideburns on 2011-11-15
As part of troubleshooting my sister's Ubuntu box, I backed up all of her home folder into a compressed tarball and moved it to one of my computers.  (all 15GB)  To do so, I created a directory /backup, moved to it and ran this:

sudo tar -cvjf marcia.tar.bz2 /home/marcia

By the time were were through, she had a squeaky-clean installation of the latest version of Ubuntu.  Now, I've used scp to put the backup back into /backup (after creating it) and I've tried several times to restore it.  If I just test the file, it shows that everything's there, but everything I've tried to restore it fails.  (BTW, this shows that they're stored with complete, absolute paths.)  Tar runs, and runs, and runs some more, but when all is said and done, not one, single, solitary file's been put back.  I've tried it using archive manager with no luck.  I've tried the obvious:

tar -xjvf marcia.tar.bz2 /

and it complained that it couldn't find / in the archive.  I've tried

tar -xjvf marcia.tar.bz2 /home/marcia

and nothing happened although it took a long time to find out.

sudo -xjvf marcia.tar.bz2 /home/marcia

is currently chugging along and ignoring the verbose switch.  I've probably overlooked something blindingly obvious, but if so, it's not obvious to me.  Any suggestions?

---

### Post by cbowman57 on 2011-11-15
I'm no expert with tar but here's an entry from my restore script

tar -xvpzf file.tar.gz -C /

Of course that's restoring a complete system to root.  Don't know if that helps but it's all I can suggest.

---

### Post by sideburns on 2011-11-15
Curiouser and curiouser:

sudo tar -xjvf marcia.tar.bz2 /home/marcia/*

gets me a number of complaints that /home/marcia/Desktop, Documents and so on aren't found in the archive, but if I look at the archive with archive manager, they're there.

---

### Post by sideburns on 2011-11-15
I just took another look at the tarball with tjvf and found another oddity: all of the paths start with home/marcia, not /home/marcia and that might be what's causing the trouble.  Any suggestions?

---

### Post by Slim Odds on 2011-11-15
> **sideburns said:**
> I just took another look at the tarball with tjvf and found another oddity: all of the paths start with home/marcia, not /home/marcia and that might be what's causing the trouble.  Any suggestions?

tar frowns on having a / at the beginning of the path (as it should frown).

```
cd /home
```Then uncompress your tarball

You're also have to sudo

---

### Post by sideburns on 2011-11-15
Here's the last thing I tried, starting in /:

sudo tar xjvf /backup/marcia.tar.bz2 -C /home

It went on and on, reporting that it was restoring files.  And, when I was done, I tried this:

df -h /home

and it reported that 23G were in use.  However, I can't actually find any of the files!  All this has been done, btw, over ssh from my Fedora box for convenience.  Should I go over to her machine, log her out and try again?  It doesn't seem reasonable, but then, most of what's happening here doesn't seem reasonable either.

---

### Post by sideburns on 2011-11-15
After logging out and in, I did some exploring in the GUI and found that tar had put everything into /home/home/marcia so I'm now merging the two folders.  And, when I'm done, I'm going to leave it that way for the time being because she's got lots of extra space and this gives me an easy way to find anything that's not where it should be.

Now, the only question is why Archive Manager didn't put things back correctly in the first place, but aside from that, I can mark this thread as solved.

---

