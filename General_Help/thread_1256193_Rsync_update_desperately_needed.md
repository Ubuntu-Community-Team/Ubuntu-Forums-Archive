---
title: "Rsync update desperately needed"
date: 2009-09-02
forum: General Help
---

### Post by pksings on 2009-09-02
Hello Canonical and all you other hard working coders and testers;

Rsync will not finish my backups, and has not for almost two weeks. I did some research and it appears that a patch or two to fix it has been committed upstream. Is this being tested/worked on ?

I'm very nervous not getting backups for this long.

Please can this be raised as a priority? I dont' think it will take much testing. I will happily volunteer if you need testers.

Thanks very much in advance, and thanks very much for all your excellent work.

The following is cut/paste from last night's backup to show the failure(s).

rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: mknod "/home/home/ \#316qF\#222.JPG&\#347\#243F\#313U\#263:7\#007500.JPG+Q\#025F\#316U\#263:9\#0051.JPG#\#221\#354F\#321U\#263:9\#0052.JPG'\#006+F\#324U" failed: Invalid argument (22)
skipping non-regular file "G-ceF\#371U\#263:9\#0056.JPG,>\#303F\#375U\#263:9\#0057.JPG0\#325AF"
skipping non-regular file "JPG'v\#244F\#335U\#263:9\#0056.JPG)C\#302F\#340U\#263:9\#0057.JPG*?\#347F\#343U\#263:9\#0058.J"
rsync: mknod "/home/home/}\#363C:2\#014IMG_1520.JPG%w\#213F	V\#263:9\#0052.JPG!\#271+F\#014V\#263:9\#0053.JPG\#024\#251\#244F\#026\#304\#273:9\#0055.JPG+\#221\#314F\#022V\#263:" failed: Invalid argument (22)
rsync: connection unexpectedly closed (5928 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]

Thanks again

PK

---

### Post by sedawk on 2009-09-02
One possible solution would be to compile it from the source yourself.
I think the only think you need first is the "build-essential" package
to be installed. If you do not have it run
```

sudo apt-get install build-essential

```

Get the latest rsync source file here:
[http://www.samba.org/ftp/rsync/nightly/rsync-HEAD-20090822-1915GMT.tar.gz](http://www.samba.org/ftp/rsync/nightly/rsync-HEAD-20090822-1915GMT.tar.gz)

Unpack it and "cd" into the new directory.
Inside the directory do this:
[CODE]
./configure
make
[CODE]
If everything works fine it takes less than 5 minutes to get a 
new rsync binary in that directory.

Check if this binary works better than the one provided by the system.
If it does copy it to some better place - e.g. /usr/local/bin/ or
/home/<backup_user>/bin/.
Do NOT overwrite the one from the system at /usr/bin/rsync !

Happy?

---

### Post by pksings on 2009-09-02
Wow, great workaround, I should have thought of that!

Seems to be working, currently copying files.

Thank you very much! The update is still welcome, but I can wait.

---

### Post by pksings on 2009-09-03
The compile and use of the downloaded version does not solve my problem, it still fails with the same error. I believe it's the rsyncd on the target server side that is producing it, but I'm not sure. 

So we still are in desperate need of a backup...

Found a workaround, has to be run as root!!! This doesn't make sense, the nightly runs as root and is failing, but I can manually run it after sudo and it works......nope, failed, just ran longer than before.....

---

