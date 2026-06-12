---
title: "backuppc"
date: 2006-06-07
forum: General Help
---

### Post by cssutto on 2006-06-07
I finally have got dapper loaded and I must say that I am impressed.

FAR FAR FAR better than breezy.

I had simple backup on breezy and thought I was backing up to an external Maxtor 200 GB drive, but when I asked it to restore, it told me that there were no backup files.  Even though the log showed it had backed up to that drive.

A real shock.

So I just downloaded backuppc.  Very interesting.  Except I am not ever going to be smart enough to set it up.

I am running a dual boot ubuntu/W2K and it appears that backuppc can back the entire machine, linux and W2K.  Great.

Except the instructions are like reading the dictionary.

Has anyone used this utility to back up a dual boot system?

CSSJR

---

### Post by Patsoe on 2006-06-07
I have no hands-on experience yet (I always just copy the important stuff to a network drive, which - I am fortunate - is backed up by a skillful system administrator), but I have been looking into this stuff, since I will have to do it myself sometime...

I think backuppc is very nice and advanced, but not worth the work of setting up for a single user. Have you had a look at rsnapshot? This seems a really nice (and trusted) tool, and also quicker to set up.

---

### Post by rdenatale on 2006-06-07
[QUOTE=cssutto]
So I just downloaded backuppc.  Very interesting.  Except I am not ever going to be smart enough to set it up.

I am running a dual boot ubuntu/W2K and it appears that backuppc can back the entire machine, linux and W2K.  Great.

Except the instructions are like reading the dictionary.

Has anyone used this utility to back up a dual boot system?

CSSJR[/QUOTE]

I don't think that it will work for that scenario.  Backuppc is really intended for backing up machines over a network, I use it to backup both my linux laptop, and my wifes windows machine to my server. So it can indeed backup both windows and linux boxen.

However, the problem with backing up the Windows side of a dual boot machine is that backuppc running on linux on that machine is never going to see the windows version of that machine on the network.

---

### Post by cssutto on 2006-06-07
Thanks to both.

You probably kept me from going to the mad house.

CSSJR

---

### Post by Patsoe on 2006-06-08
One more addition, you may also be interested in rdiff-backup (I couldn't remember this name yesterday :)). It is in the main repository of Ubuntu, which you may find a reassuring thing too.

---

