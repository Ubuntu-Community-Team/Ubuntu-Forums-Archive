---
title: "Free space"
date: 2011-03-04
forum: General Help
---

### Post by Dsky on 2011-03-04
I'm running out of space...

i've a little netbook with ubuntu... what can i delete/unistall?

i've already unistalled a lot of things...

please tell me all that i can delete without compromise the so

---

### Post by dabl on 2011-03-04
How large/small is the partition that Ubuntu is installed on?  The default OS doesn't come with lots of useless pieces, so if your partition is too small, you're really only delaying an inevitable re-partitioning job by twiddling with package removals.

Having said that, the archived log files (not the active ones!) in /var are expendable, although they will be regenerated over time.  I suppose man files are expendable, if you don't ever use them -- readmes are likewise.  But text files are inherently very small -- a few dozen kilobytes would be a big one.

You can use apt to remove --purge any packages that you never intend to use.  But again, they're not large in filesize.

---

### Post by seawolf167 on 2011-03-04
> **dabl said:**
> if your partition is too small, you're really only delaying an inevitable re-partitioning job by twiddling with package removals

+1 

If you are dual booting or have too small a / partition, removing packages and a couple MB of logs & man pages isn't going to delay the disk space warnings for long

---

### Post by Dsky on 2011-03-05
this netbook has 2 hard disks.

1 of 16gb very slow and 1 of 4gb very fast...

i tried to install the so on the 16gb one but it is really slow..

so im on the 4gb... and i left only 40mb of space...

can you pls write me some commands to delete/purge those files you think are useless

---

### Post by wiggly81 on 2011-03-05
does the netbook have SD card slots, it could be that the best option is to have an SD card installed and to use it as the /home this will free up space on the 4GB hard drive.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

you could aslo do the same using a External Hard Drive, however i guess that mmight not always be the best way when using a netbook because it would make it less portiable.

---

### Post by Dsky on 2011-03-05
i just could move home on the other partition right?

but... how much space does home use?

---

### Post by wiggly81 on 2011-03-05
yes you could move it to other partition...
my /home is around 1GB so not a huge diffrence but you could do the same with things like /var and /tmp and /usr aswell, /usr on my system is over 4GB, i dot have a lot installed at the moment.
It may be a bit fiddly to change the location of all mounts but it may solve your problem

---

### Post by Dsky on 2011-03-05
thanks!!

i did that... now i've 500mb more...

moving var and tmp on the slow hd could the pc become slower?

---

### Post by oldos2er on 2011-03-05
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Dsky on 2011-03-06
how can that help me?

thanks :)

---

### Post by lithopsian on 2011-03-06
Use the du command.  It will tell you how much space is being used where, for example /home.  Use --max-depth 1 for a first pass.  /home is as big as you make it.  In your case I suspect not very big because Ubuntu will take about 3GB as soon as you install it.  There is probably about a gig of that you could delete fairly easily, but it will take some effort.  Just go through and delete applications you don't plan to run.  A few are big, many area small.  Delete enough and you'll get extra benefit by being able to remove substantial libraries too.

/usr will probably be taking most of your space, that is Ubuntu, programs, libraries, and themes.  If /var is more than a couple of hunded meg then clean it up.  /lib may be big if you have multiple kernels installed but otherwise should be less than 100MB.

So you'll have to pick some things to move to the slow disk, or to somewhere else.  /home is a good candidate.  /var and /etc aren't really because they tend to be full of stuff getting read and written all the time.  Move /opt if it has anything in it, probably /tmp too.

---

