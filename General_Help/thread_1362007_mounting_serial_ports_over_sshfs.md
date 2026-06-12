---
title: "mounting serial ports over sshfs"
date: 2009-12-22
forum: General Help
---

### Post by Leporello on 2009-12-22
Hi,

I would like to have access to the serial ports on my desktop machine from my laptop. On the desktop, the serial ports are on /dev/ttyS0 and /dev/ttyS1. It seems to me that I should be able to mount the serial ports on my laptop using sshfs. So here's what I have done, to mount /dev on the remote machine on my laptop:

```

cd ~/
mkdir mnt/thor_dev
sshfs djones@192.168.0.103:/dev/ mnt/thor_dev/

```

So far so good. Now my understanding is that I will have the same permissions on mnt/thor_dev as user djones has on the desktop (at 192.168.0.103). On the desktop, djones is a member of group dialout, which has read and write permissions to the serial ports. So I should have the same permissions on my laptop. Unfortunately, when I try to use minicom on the laptop, I get the following:

```

~$ minicom thor_port1
minicom: cannot open /home/djones/mnt/thor_dev/ttyS0: Permission denied

```

This is something I've never been quite clear on: if a user runs a program, does that program then have the same permissions as that user? So shouldn't minicom have the same permissions that I do? Then what am I doing wrong here? By the way, this is the output of ls -l on ~/mnt:

```

~$ ls -l mnt/thor_dev/
...blah blah...
crw-rw---- 1 root dialout 0, 0 2009-12-22 12:12 ttyS0
crw-rw---- 1 root dialout 0, 0 2009-12-22 12:12 ttyS1
...blah blah...

```

---

### Post by Leporello on 2009-12-22
Update: I tried chmod'ing both /dev/ttyS0 and /dev/ttyS1 as a+rw on the remote machine. But I still get the same permission denied error. Is there something special about the serial ports that would make mounting them over sshfs impossible?

---

