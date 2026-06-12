---
title: "Laziness/frustration rsync"
date: 2009-09-19
forum: General Help
---

### Post by nothingspecial on 2009-09-19
I know how to read the manual.

I know what I`m doing in most cases.

However, I`m really tired, p*****d off, amongst other things.

My server went down yeaterday.

It has 2TB`s of stuff on it. I got it back up and running and copied 45000 + files and it went down again. I didn`t know what I`d copied and what I`d not so I got it back up and running again, and started copying again.

The bloody thing crashed again!!!!

After copying 43,172 files ](*,)

So I have a few files out of loads that haven`t been copied but I don`t know which ones they are.

I know that rsync can do this, but I`m not sure of the exact syntax and really don`t want to **** this up.

The original directory is /media/server/

The backup directory is /media/backup/

If anyone knows the correct syntax to copy only the missing files I`d be eternally gratefull.

Failing that I`ll just look myself tommorow.

Thanks

---

### Post by Liolikas on 2009-09-19
[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)
Skip boring part read how to set up server and most important Using Rsync Itself first few lines and command.

---

### Post by aysiu on 2009-09-19
I believe it would be ```
rsync -av /media/server/* /media/backup/
``` I'm not 100% sure on the slashes, though. It may end up creating a /media/backup/server subfolder.

---

### Post by nothingspecial on 2009-09-19
> **aysiu said:**
> I believe it would be ```
rsync -av /media/server/* /media/backup/
``` I'm not 100% sure on the slashes, though. It may end up creating a /media/backup/server subfolder.

That`s promising. Thankyou.

I feel a bit better now.

Of course any other advice is appreciated but I reckon I can handle this now.

Jeez I was annoyed a few minutes ago.

Thanks both of you,

---

### Post by StuartN on 2009-09-19
> **nothingspecial said:**
> If anyone knows the correct syntax to copy only the missing files I`d be eternally gratefull.

It is quite literally "rsync -<options> source/ destination/" which will be something like
```
rsync -avh /media/server/ /media/backup/
```
but you might (or possibly not given the crashes!) want to run it first with the n option, "rsync -avhn source destination > sync.txt", to produce an archive run, verbose output, human readable, no actual file transfer (dry run) to record what files would be transferred.

(Note that archive mode -a is equal to -rlptgoD meaning recurse, copy symlinks as symlinks, preserve permissions, times, group and owner, preserve device/special files).

Edit: trailing slashes required

---

### Post by nothingspecial on 2009-09-19
Thankyou for your reply.

The stupid thing crashed again, it is obviously broken.

Further investigation shows that cp copies one directory at a time.

This means that all the missing files are in /media/server/music/flac

In the interests of getting to bed and having a happy wife I am going to plug all the drives into my netbook and copy /flac again.

Tommorow I shall smash the ******* server into pieces and find a new one.

And I shall also post the correct syntax here.

Thanks again but the original problem is obviously a hardware one and can only be solved with new hardware.

---

### Post by nothingspecial on 2009-09-21
Ok so I`m using my little broken netbook as my new server. It actually seems to work better. 

The command I needed was rsync -avz /media/server/ /media/backup/

Just in case anyone sees this in the future.

Cheers for helping.

---

### Post by raymondh on 2009-09-21
I followed this thread with interest.  Excellent news and thanks for the syntax.

Because of scenarios like this, I now use (thanks to a reco from a friend) a 2-prong approach.  Rsync (with grsync - the GUI) to do a regular sunday back-up..... and [PING]("http://ping.windowsdream.com/").  Sure, I may just waste space with PING but it does make sense rather than re-installing.  I also have PING images on an external HD, away from my main HD.

Am glad you have your server back on.  Happy Ubuntu-ing.

---

### Post by badger_fruit on 2009-09-21
> **nothingspecial said:**
> Tommorow I shall smash the ******* server into pieces and find a new one.

Amen brother!

Glad you found a solution, not sure if it's any use now but I wrote a little script which can be added to your crontab ...

```

#!/bin/sh
LOG_FILE=/home/badger_fruit/bin/$(date '+%Y-%m-%d')-backup.log
echo >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
date >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
echo "Backup ==> bgrsvr-x" >> $LOG_FILE
rsync -avz /source/folder/  /target/folder/ >> $LOG_FILE 2>&1
echo "------------------------------" >> $LOG_FILE
echo "End" >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
echo "   " >> $LOG_FILE

```Nothing fancy - runs every hour to make sure it catches any new files (this backs up my photos) and outputs the result to a log file which changes name each day (IIRC lol!)

---

