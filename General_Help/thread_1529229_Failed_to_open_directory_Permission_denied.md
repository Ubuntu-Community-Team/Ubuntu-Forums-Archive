---
title: "Failed to open directory: Permission denied"
date: 2010-07-11
forum: General Help
---

### Post by Bucky Ball on 2010-07-11
Hi all,

HELP!! I switched on my machine this morning and two of the partitions seem to have permissions changed. I click and get the message above:

```
Failed to open directory "Disk Name": Permission denied
```

... where 'disk name' is the name of my partition. Only thing I can think of is there was an unhealthy shutdown or some such. I do remember having to switch machine off manually the other day as it locked up at shutdown and this may have left the partitions open. 

I am ruling out hardware failure for now as the two partitions in question (the many others are functioning fine) are on different physical drives. Sees them in Gparted, just can't mount them. Machine boots fine, click on partition, get error message.

Hoping someone can help. I desperately need to use the partitions as I am flat out building a website for a local club at the moment and can't really have any delays right now. Too bad; looks like I've got one!! 

Here's hoping someone can help and thanks in advance.

---

### Post by CharlesA on 2010-07-11
Please post the output of this:

```
ls -ld "Disk Name"
```

---

### Post by Bucky Ball on 2010-07-11
Results for the two partitions in question:

```
bucky@Studio:~$ ls ld "DISK1-MISC"
ls: cannot access ld: No such file or directory
ls: cannot access DISK1-MISC: No such file or directory
bucky@Studio:~$ 
bucky@Studio:~$ ls ld "AudioRecord"
ls: cannot access ld: No such file or directory
ls: cannot access AudioRecord: No such file or directory
bucky@Studio:~$
```Am looking for clues regarding improperly unmounted partitions ... thanks for your help. :)

---

### Post by CharlesA on 2010-07-12
Forgot the dash.

Did you have them automatically mount, or do you need to create a folder and mount it there?

---

### Post by Bucky Ball on 2010-07-12
I was right the first time. Incorrect shut down.

I tried:

```
sudo mount /dev/sda5
```

... and got error message telling me if I had Windows, correctly eject device in that, if not force mount. I booted into Windows then shutdown completely (not restart) and all is well. Working away happily. 

Cheers and thanks for your help. ;)

---

