---
title: "Gzip running in background... taking up disk space...?"
date: 2010-02-02
forum: General Help
---

### Post by rob_l_f on 2010-02-02
Hi,

This morning I had a strange thing happen - I suddenly recieved a warning saying that I only had 300MB disk space left, so I check df and it confirmed this - except something was churning my hard drive, the light was on almost solid.  So I checked df again and it had gone down a few MB!  top then showed that for some reason gzip was using 40% of my CPU, which presumably was what was causing the drive activity, but what the hell was it doing?  I was able to kill the process as root (might not have been the most sensible thing to do but it was going to fill my drive anyway), but all I was doing at the time was using netbeans, rhythmbox and firefox (on Karmic) - does anyone have *any* idea what that was?

Thanks very much.

---

### Post by squaregoldfish on 2010-02-02
First random guess - have a look in /var/log - the system compresses old log files automatically, and there may have been a process that went on a logging spree.

Check the subdirs too!

Steve.

---

### Post by rob_l_f on 2010-02-02
Thanks squaregoldfish - I had a look, but there were no gzips in those folders accessed or modified today - not sure if thats a indication that that wasn't it or not but I guess not...

---

### Post by squaregoldfish on 2010-02-02
Unfortunately my first random guess was also my only random guess. I'm sure there's some disk usage analyser software somewhere in Ubuntu - it's probably worth spending a bit of time with that to hunt down where all your space has gone.

Steve.

---

### Post by rob_l_f on 2010-02-03
I'm using du to try and figure out where all the space has gone... annoyingly this happenned again today and filled the drive, but I don't know what to delete to rectify this.  I tried using ls to find anything that was modified today but that's not yielding anything useful.

The process is still running now, as root (even though the disk is full), does anyone have any idea how I can figure out what started this process?

Cheers

---

### Post by squaregoldfish on 2010-02-03
If you run ps -eaf on a very wide terminal, you'll get to see all the command lines of the processes being run.
```

ps -eaf |grep gzip
```

will hopefully give you some idea of what's happening.

Steve.

---

### Post by rob_l_f on 2010-02-03
Ah... solved it, this was actually me being quite stupid...  it was actually sbackup, something which I was positive I had not scheduled but obviously had.  In the last few days I've copied a load of images to one of the folders covered by sbackup so it has been churning away making copies of these massive directories.  Oops!  Thanks anyway squaregoldfish.

---

