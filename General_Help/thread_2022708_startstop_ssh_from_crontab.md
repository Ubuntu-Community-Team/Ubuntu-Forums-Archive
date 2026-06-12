---
title: "start/stop ssh from crontab"
date: 2012-07-11
forum: General Help
---

### Post by lightbox on 2012-07-11
Hi, I'm using 12.04 LTS server, and i want to turn on/off ssh in a crontab in order to open a small window of time for my backup (via rsync/ssh) to connect.

I figured it'd be as easy as putting

service ssh start
service ssh stop

into the appropriate root crontabs (using "crontab -e" as root), but doing that creates an email from the crontab daemon that says:

/usr/bin/service: 123: exec: start: not found

i tried "/etc/init.d/ssh start" (/stop) as well, same error

So then i tried creating my own bash script to properly initialize the shell:

----startssh.sh-----
#!/bin/bash
source /etc/profile
service ssh start
--------------------

and it, again, outputs the same error to an email:

/usr/bin/service: 123: exec: start: not found

what am I doing wrong?? How can i start/stop ssh at certain times "the proper way"  i know I could just run "/usr/sbin/sshd -D" myself, but thought it was better to use the proper startup/shutdown scripts...

Thanks!
James

---

### Post by Cheesemill on 2012-07-11
Entries in crontab don't have a full environment set up. Try using:
```
/usr/sbin/service ssh start
```
and
```
/usr/sbin/service ssh stop
```

---

### Post by lightbox on 2012-07-11
> **Cheesemill said:**
> Entries in crontab don't have a full environment set up. Try using:
```
/usr/sbin/service ssh start
```
and
```
/usr/sbin/service ssh stop
```

Same thing, /usr/bin/service is simply a symlink to  /usr/sbin/service

i know its running the service script, but its soemthing in the service script that is failing (like the start or exec) because it doesnt have the appropriate environment initialized... i thought thats what doing "source /etc/profile" would do?

/usr/sbin/service: 123: exec: start: not found

---

### Post by papibe on 2012-07-11
Hi lightbox.

This is a tricky one.

'crontab' has a limited environment, included a very short path. Although 'service' is on this very basic path, 'service' is actually an script that that calls other scripts.

**start, stop and status** are not real parameters, but other programs that live on /sbin, which is **not** in the limited crontab path.

You can check it yourself by doing:
```
$ ls /sbin/stop /sbin/start /sbin/status 
/sbin/start  /sbin/status  /sbin/stop

```
The easy solution then, is to expand the path as the first line of your crontab, so that includes /sbin. For instance:
```
# m h  dom mon dow   command
PATH=/usr/sbin:/usr/bin:**[COLOR="Red"]/sbin[/COLOR]**:/bin
*/1 * * * * service mysql stop

```
I hope that helps, and let us know how it goes.
Regards.

---

### Post by steeldriver on 2012-07-11
this is a bug I think -

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1008892](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1008892)

try setting  PATH="/sbin:$PATH" explicitly

EDIT: oops papibe beat me to it

---

### Post by sanderj on 2012-07-11
> **lightbox said:**
> ...

/usr/bin/service: 123: exec: start: not found

what am I doing wrong?? How can i start/stop ssh at certain times "the proper way"  i know I could just run "/usr/sbin/sshd -D" myself, but thought it was better to use the proper startup/shutdown scripts...

Thanks!
James

Have you tried the old-skool

```
/etc/init.d/ssh stop
```

in your root's crontab?

---

### Post by lightbox on 2012-07-11
> **papibe said:**
> Hi lightbox.

This is a tricky one.

'crontab' has a limited environment, included a very short path. Although 'service' is on this very basic path, 'service' is actually an script that that calls other scripts.

**start, stop and status** are not real parameters, but other programs that live on /sbin, which is **not** in the limited crontab path.

You can check it yourself by doing:
```
$ ls /sbin/stop /sbin/start /sbin/status 
/sbin/start  /sbin/status  /sbin/stop

```
The easy solution then, is to expand the path as the first line of your crontab, so that includes /sbin. For instance:
```
# m h  dom mon dow   command
PATH=/usr/sbin:/usr/bin:**[COLOR="Red"]/sbin[/COLOR]**:/bin
*/1 * * * * service mysql stop

```
I hope that helps, and let us know how it goes.
Regards.

Yup that did it!  Thank you so much:

```

PATH=/usr/sbin:/usr/bin:/sbin:/bin
4   4 * * *     service ssh start
30  4 * * *     service ssh stop

```

James

---

### Post by papibe on 2012-07-11
:D Great!

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")) when you have the chance.

Regards.

---

