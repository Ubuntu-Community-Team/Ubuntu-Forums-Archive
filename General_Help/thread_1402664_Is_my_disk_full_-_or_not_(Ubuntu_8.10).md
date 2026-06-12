---
title: "Is my disk full - or not? (Ubuntu 8.10)"
date: 2010-02-09
forum: General Help
---

### Post by rsgrimes on 2010-02-09
I've been getting error messages indicating my disk might be full, but I don't really think it is.    It is so bad that I could not log on via Gnome, but fortunately I was able SSH into my box.  Can't even create a directory!

So I did the df command:

```
vree:~/tmp$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             132G   57G   69G  46% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  124K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.7M  502M   1% /dev
tmpfs                 505M   24K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
```Hmm...  Doesn't look full to me.  I've looked at the HOWTO, but it doesn't seem it applies to my situation, as df reports 69G available!  Or am I confused?

Any ideas?  

TIA,
-Bob

---

### Post by iponeverything on 2010-02-09
What are the error messages that you are getting?

---

### Post by rsgrimes on 2010-02-09
Very basic: anything that would create something fails like the following:

```
$ mkdir /tmp/dummy
mkdir: cannot create directory `/tmp/dummy': No space left on device
```

Thanks!

---

### Post by rnerwein on 2010-02-09
hi
try: df -i 
may be you run out of inodes. or are have you played with quotas ?
ciao

---

### Post by rsgrimes on 2010-02-10
Yeah, that seems to be it - no inodes available:

```
vree:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdb1            8773632 8773616      16  100% /
tmpfs                 129117       4  129113    1% /lib/init/rw
varrun                129117      59  129058    1% /var/run
varlock               129117       3  129114    1% /var/lock
udev                  129117    4941  124176    4% /dev
tmpfs                 129117       1  129116    1% /dev/shm
lrm                   129117      17  129100    1% /lib/modules/2.6.27-11-generic/volatile

```

Of course, this was after deleting a few files...

So, assuming the huge number of inodes are extraneous, how do I figure out where they are?

Or if they end up largely as valid, how does one increase their number? 

That number seems awfully bogus...

Thanks
-Bob

---

### Post by philinux on 2010-02-10
[http://stackoverflow.com/questions/653096/howto-free-inode-usage](http://stackoverflow.com/questions/653096/howto-free-inode-usage)

---

### Post by rsgrimes on 2010-02-10
Thanks for the link!

And I found my problem!  I have been using BackInTime (a poor man's Time Machine) on my workstation, and it was taking snapshots on the server; I haven't constrained it a bit, and so it has generated quite a few files - I'm currently counting them, and it's up to almost 4 million - and counting!

That's what you get with "set and forget" tools!  (No, that's not a criticism of BackInTime!).

Thanks,
-Bob

---

