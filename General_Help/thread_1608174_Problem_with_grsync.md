---
title: "Problem with grsync"
date: 2010-10-28
forum: General Help
---

### Post by M_Mynaardt on 2010-10-28
Hi!

I just tried using grsync on my desktop with Ubuntu 10.10 and it is acting quite strange.

Now, the probable reason is that I reinstalled it from scratch (long story) and reinstalled my software and restored my data, which is a pain.  And because I was tired and irritable when I did that, I did not enter my used ID and such exactly the same as it was previously.  I'm not sure if that's the problem or not.

Now here's the problem...

I use grsync to sync my data files between my desktop, netbook, and laptop.  To date, grsync has worked just fine.  But not now on my desktop.  Instead of synchronizing files between /myname/Desktop/ and /media/USBcopy/Desktop/ what grsync now does is create a whole new copy of  /myname/Desktop/ as /Desktop/ in the back up folder.  It's never done that before!  And it only synchronizes to that new folder.

So before, if I had the following on my Desktop:
[INDENT]
/myname/Desktop/finances/
/myname/Desktop/recipes/
/myname/Desktop/STUFF/
[/INDENT]
Then grsync would faithfully sinchronize with:
[INDENT]
/USBcopy/Desktop/finances/
/USBcopy/Desktop/recipes/
/USBcopy/Desktop/STUFF/
[/INDENT]

But now, what I get instead is:
[INDENT]
/USBcopy/Desktop/finances/
/USBcopy/Desktop/recipes/
/USBcopy/Desktop/STUFF/
[COLOR="DarkRed"][B]/USBcopy/Desktop/Desktop/finances/
/USBcopy/Desktop/Desktop/recipes/
/USBcopy/Desktop/Desktop/STUFF/[/B][/COLOR]
[/INDENT]

I can't for the life of me figure out why it's creating duplicates like that now, when it didn't before.  I _think_ it might possibly be because I actually misspelled my name when I created my user ID when I installed Ubuntu 10.10.  I did say I was tired, right?  Does anyone know if that would affect grsync's behavior?

If not, can anyone offer any explanation as to why grsync would now insist on creating a duplicate /Desktop/ folder structure in my USB copy when it didn't do that before?

I think there must be something about Ubuntu 10.10 that's causing this.  I had the same result synchronizing my files on my laptop.  Instead of just making copies of the desktop files, it's using a straight copy of /Desktop/ in the target directory, which it didn't used to do.  It's synchronizing and backing the files up, thankfully, but not in the file structure I was expecting.

Thanks for anything anyone can tell me!

---

### Post by falconn19 on 2010-10-29
I had a similar problem with grsync as well.   I used to rsync fine in 10.4 using the follow dirs:

/home/useraccount/data  to  /media/backupdrive/backup

Now when I run my grsync it copies to a new directory via:

/home/useraccount/data  to  /media/backupdrive/backup/data

Looks like it is copying the directory instead of the just the files in the directory.

---

### Post by baddnady23 on 2010-10-29
I'm not sure if grsync is sensitive to it or not, but when using rsync in the command line interface, having a trailing slash at the end of the command determines if it copies the directory *and *its contents or just the directory.

See a previous post about rsync that addresses the trailing slash (post #10):
[http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

---

### Post by M_Mynaardt on 2010-10-29
> **falconn19 said:**
> I had a similar problem with grsync as well.   I used to rsync fine in 10.4 using the follow dirs:

/home/useraccount/data  to  /media/backupdrive/backup

Now when I run my grsync it copies to a new directory via:

/home/useraccount/data  to  /media/backupdrive/backup/data

Looks like it is copying the directory instead of the just the files in the directory.

Yes, it is copying the directory, which is a bit odd.  It still seems to be backing and synchronizing the files.  But I don't know why it suddenly started using a different file structure in the target directory.  Oh well; a little bit of a pain, but it's better than having all my data nuked!

---

### Post by M_Mynaardt on 2010-10-29
> **baddnady23 said:**
> I'm not sure if grsync is sensitive to it or not, but when using rsync in the command line interface, having a trailing slash at the end of the command determines if it copies the directory *and *its contents or just the directory.

See a previous post about rsync that addresses the trailing slash (post #10):
[http://ubuntuforums.org/showthread.php?t=238672](http://ubuntuforums.org/showthread.php?t=238672)

Yes, grsync does add the trailing "/" at the end of a directory name.  For some reason, though, instead of just copying a directory's files in the target directory as it did before, now it's copying the entire directory into the target directory.  It's still synchronizing files, mind.  So at least my data hasn't been nuked.  I just think it's odd that grsync started doing file structures differently.  The only thing that's different now is that I'm using Ubuntu 10.10.  Oh well, it could be worse; at least it hasn't torched any data!

---

