---
title: "Fix swap partition"
date: 2011-01-14
forum: General Help
---

### Post by vacco on 2011-01-14
swapon -s return no swap partition for my Ubuntu system. ```
Filename				Type		Size	Used	Priority

```
I do have a swap partition, but from what I understand, the Slackware install I intended to use with the same swap partition have probably changed the UUID or something. This is my blkid entry for the swap partition: ```
/dev/sda8: UUID="bac99b00-3241-4faf-94d9-197c94cfd94d" TYPE="swap"
```

I can right click the swap partition in Gparted and select swapon, which will then cause swapon -s to show it like this:
```
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	4227068	0	-1

```
It is gone after a reboot though. swapon -a, no matter if I have enabled swapon in Gparted or not, always gives this feedback:
```
swapon: cannot find the device for UUID=c6cd4dc1-cfa5-46f2-9bf7-4dd91fc1baeb

```

swapon -s displays sda8 as swap partition immediately after startup in Slackware, with no further action required.

Could anyone please guide me in order to get my swap partition working automatically with Ubuntu again? I am much more concerned with having things work in Ubuntu which I use on a daily basis than Slackware which I installed with the intention of just playing around.

---

### Post by Dave_L on 2011-01-14
Does your /etc/fstab contain this line?

```
UUID=bac99b00-3241-4faf-94d9-197c94cfd94d	none	swap	sw	0	0	# /dev/sda8
```

If not, try adding it. I would make a backup copy of the file first.

---

### Post by vacco on 2011-01-14
Thank you very much! I replaced the UUID for my swap partition in fstab with the one I got from swapon -s, rebooted, and now things seem to be back on track. Even the hibernate button is back :D Now I just hope this will keep my system from crashing all the time.

Is it impossible to use the same swap partition for both of the two Linux systems on my hard drive?

---

### Post by vacco on 2011-01-14
I also thought I would link to my other thread about this issue, in case anyone should come by with the same problem: [http://ubuntuforums.org/showthread.php?t=1662934](http://ubuntuforums.org/showthread.php?t=1662934)

---

