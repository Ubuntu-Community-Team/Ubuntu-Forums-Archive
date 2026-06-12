---
title: "Pidgin Crashes"
date: 2009-11-24
forum: General Help
---

### Post by pcman312 on 2009-11-24
I have been plagued with pidgin crashing on me periodically. I haven't been able to find a pattern indicating what could be causing the problem.

I ran pidgin with the -d option and piped the stdout and stderr to files. Unfortunately, I am not familiar with the inner workings of pidgin, so I can't tell for sure what is causing the problem. I did however notice this at the end of the error output:

```
E: client-conf-x11.c: XOpenDisplay() failed
W: core-util.c: Failed to open configuration file '/home/[censored]/.pulse/client.conf': Too many open files
W: client-conf.c: Failed to open configuration file '/etc/pulse/client.conf': Too many open files
W: shm.c: Failed to read /dev/shm/: Too many open files
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
E: authkey.c: Failed to open cookie file '/home/[censored]/.pulse-cookie': Too many open files
E: authkey.c: Failed to load authorization key '/home/[censored]/.pulse-cookie': Inappropriate ioctl for device
E: shm.c: shm_open() failed: Too many open files
E: shm.c: shm_open() failed: Too many open files
E: shm.c: shm_open() failed: Too many open files **[this repeats about 500 times]**
E: mainloop.c: ERROR: cannot create wakeup pipe
**
ERROR:pulsemixerctrl.c:215:gst_pulsemixer_ctrl_open: assertion failed: (c->mainloop)
```
Unfortunately, there aren't any timestamps on the error log so I don't know when each event happened.

Here's a link to the two output files:
[http://www.athemon.com/pidgin.tar.gz](http://www.athemon.com/pidgin.tar.gz)

For reference:
Ubuntu 8.10
Pidgin 2.6.3
Pidgin has the following accounts:
1 AIM
1 MSN
1 Gmail (XMPP)
1 Jabber account for work (XMPP)
I haven't noticed any pattern regarding when it crashes, including what accounts are active (since all 4 are active all the time when I'm at work), nor who I'm talking to nor how many people I'm talking to.

Thanks in advance for the help :) :popcorn:

---

### Post by DapperMe17 on 2009-11-24
Try installing the updated version of Pidgin from getdeb.com.

It's a .deb file, & will install when double clicked.

---

### Post by pcman312 on 2009-11-25
I'm already running the latest version (1:2.6.3-1ubuntu1~pidgin1.8.10.1 according to synaptic and 2.6.3 according to pidgin). And I think you meant getdeb.net ;) :P

---

### Post by pcman312 on 2009-12-01
Well, I hate to bump a thread, but I'm still having this problem and it's starting to piss me off.

---

### Post by crm71 on 2009-12-01
> [...]failed: Too many open filesLooks like pidgin and pulseaudio calls within it are failing to get any free file handles on open.  What else is breaking besides pidgin? :shock:

Are you running processes like torrents, web servers, etc. that may be keeping an excessive amount of files open?  Have you tried running pidgin only with nothing else running after boot up?

You may also want to look into /etc/security/limits.conf or maybe ulimit.

---

### Post by pcman312 on 2009-12-01
> **crm71 said:**
> Looks like pidgin and pulseaudio calls within it are failing to get any free file handles on open.  What else is breaking besides pidgin? :shock:

Are you running processes like torrents, web servers, etc. that may be keeping an excessive amount of files open?  Have you tried running pidgin only with nothing else running after boot up?

You may also want to look into /etc/security/limits.conf or maybe ulimit.
The machine I'm using is a development machine for the software we make. I have a number of applications running while I'm working, including but not limited to: glassfish, mysql, eclipse, firefox, gnome-terminal, and of course pidgin. All of this together takes up quite a lot of memory (2.5+ GB, I have 4 in this machine). I turned off the sounds in pidgin, hopefully by not having any sounds at all it won't need to access pulseaudio and not crash on me.

---

### Post by crm71 on 2009-12-01
Out of curiosity, what are the output of the following during your regular use?

```
cat /proc/sys/fs/file-max
cat /proc/sys/fs/file-nr
sudo lsof | wc -l
```

---

### Post by pcman312 on 2009-12-02
> **crm71 said:**
> Out of curiosity, what are the output of the following during your regular use?

```
cat /proc/sys/fs/file-max
cat /proc/sys/fs/file-nr
sudo lsof | wc -l
```

```
356479
```
```
6272	0	356479
```
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /[homedir]/.gvfs
      Output information may be incomplete.
7619
```

I can write a simple script to output the results from lsof to a file periodically and try to correlate with the logger I have set up for pidgin indicating when it starts/stops/etc.

---

