---
title: "udevd-work[XXX] open /dev/null failed: No such file or dir"
date: 2010-08-27
forum: General Help
---

### Post by kretyn on 2010-08-27
Hi,

I've been having this error over a month now. When I boot up my Ubuntu 10.04 I get ```
udevd-work[304] open /dev/null failed: No such file or directory
``` and it stops for about 30s. I've check that dir it exists and is readable-writeable (chmod 666).

Few days ago I also had problem with sound - there wasn't any, and couldn't restart laptop. After rebooting it the hard way (holding power button) everything was fine.

I've posted the same issue on Polish Ubuntu Forum also month ago. Either nobody knows what's going on, or I've posted in wrong section. Anyway, please help.

Cheers,
Dawid

---

### Post by kretyn on 2010-08-28
Please?

---

### Post by kretyn on 2010-09-02
Can somebody at least say that he read what I wrote in thread and don't know what's that? I know that bumping up thread is wrong thing to do, but what else can I do?

---

### Post by spjackson on 2010-09-02
/dev/null should look like this.
```
crw-rw-rw- 1 root root 1, 3 2010-09-01 17:02 /dev/null
```Note in particular the 'c' at the start of the line and 1, 3 between the group and the timestamp. If it doesn't look like that, then something has broken it. Is anything else broken in /dev ? Your sound problem could possibly have been down to that.

If you identify anything broken in /dev, I suggest that you consider backing up important data and re-installing Ubuntu.

Edit: I now see that others have experienced this. See for example [http://ubuntuforums.org/showthread.php?t=1479732](http://ubuntuforums.org/showthread.php?t=1479732)

---

### Post by JG6_oddball on 2011-01-27
is anyone here using a 500gig samsung HD?

---

### Post by col48 on 2011-03-06
I see the same thing every boot.  My /dev/null looks as per post #4.

Irritating but not a problem (I hope!).

---

### Post by LordNodens on 2011-05-02
Same problem here after upgrading to 11.04. Sometimes it appears, sometimes it doesn't.

---

### Post by dazz100 on 2011-06-29
Hi
I have the same problem on the same version. 

I have found a bug report for this here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575333]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575333")

Dazz

---

