---
title: "Upstart Help Needed"
date: 2010-01-28
forum: General Help
---

### Post by jluce on 2010-01-28
Is there a good document anywhere on the intricacies of getting a script to start at boot time?

I have a program that will not run as root (checks for UID = 0) but will run as a daemon, however, I would like to have stdout and stderr go to files.

So, the two tasks are to have it think that root is not starting the program on boot and to have these outputs go to a file.

Hmmm, sorry for the redundancy. I do not see any real cook book methodology to do this. Nor do I see a real good instructional document.

If I use the following in the prog.conf file in /etc/init:

exec su - username -c 'progname options'

it does not start at boot, but will run if from a console I type
"start prog" where prog is of prog.conf

When I try to redirect using >> filename 2>&1 in the prog.conf file it doesn't start at all either way.

Thanks in advance for your help.

---

### Post by spiderbatdad on 2010-01-28
have a look at the readme file in /etc/init.d and in /etc/rcS.d
you should get messages in /var/log/daemon.log, and the like.

---

### Post by john newbuntu on 2010-01-29
If you decide to use upstart, try the su command giving the full path:
exec /bin/su .....
Can't think of anything else other than debugging it one tiny step at a time.  Also, throw in the start and stop runlevels in your batch just to be safe.

The other option is always the System V way as suggested by spiderbatdad, the simplest being adding your command to /etc/rc.local

---

### Post by jluce on 2010-01-29
Thanks for the info... I guess upstart doesn't leave a trail of what scripts it ran...

The problem with using rc.local is that I want the task to respawn if it dies... any help with that?

---

### Post by john newbuntu on 2010-01-30
You could write a bash script that acts as a daemon and implement the trap command in the script to restart itself if it is interrupted.
The other way would be to have a wrapper script poll for the main process and restart it if it is killed.

---

