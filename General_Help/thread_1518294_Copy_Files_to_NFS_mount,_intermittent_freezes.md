---
title: "Copy Files to NFS mount, intermittent freezes"
date: 2010-06-26
forum: General Help
---

### Post by sixy on 2010-06-26
I am running Ubuntu 10.04 on my main desktop, and I just finished building a FreeNAS server 0.71 to house my data. My share is on FreeNAS at /mnt/monster and I mounted it in Ubuntu at /media/Monster using the command: 
```
sudo mount -t nfs 192.168.1.100:/mnt/monster /media/Monster
```

Everything appears to work fine, except that when I'm copying files to the share, my PC will freeze intermittently. The mouse stops moving, screen won't refresh, etc. Usually it'll only freeze for 2-10 seconds, you can move for 10 seconds and then it freezes again (rinse, repeat). Occasionally it will freeze for several minutes though also.  My CPU usage is not high at all (<10% on one core)

How can I correct this, even if it means slowing down the transfer a little?

Thanks in advance!

Update: I thought I should mention I'm copying through the GUI. I will try a command-line after this transfer finishes and see if I get different results.

---

### Post by sixy on 2010-06-26
A copy from the terminal causes the freezes also.

---

### Post by ptviperz on 2010-07-21
I'm having the exact same problem, this only happened after I upgraded from 9.10 to 10.04. 9.10 handled large files over NFS perfectly

I'd love some idea of where to look for the problem

---

### Post by hatsch on 2010-07-22
hm, same problem here on kubuntu 10.4 with unfs on ubuntu 10.4 server

no idea what it could be

---

### Post by rubylaser on 2010-07-22
Have you tried to add the mout to /etc/fstab and use some different mount options?
```
sudo nano /etc/fstab
```

And paste...

```
192.168.1.100:/mnt/monster /media/monster nfs intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,tcp 0 0
```

And what export options is FreeNAS using? (Sorry, I don't use this for my NAS, so I'm not sure if it shows you these in the GUI).  Is it something like this?
```
rw,no_root_squash,async
```

---

### Post by bludy on 2010-08-06
I'm having the same problem.  Does anyone have a resolution to this issue?  It's pretty annoying isn't it?


Thanks!

---

### Post by hickwillie on 2010-08-19
Same problem here, the change in fstab settings didn't work for me.  I have the resource monitor on my panel and it is kinda weird.  Whenever I start the copy, it will go for about 300-400MB before it ever hits the network.  Once it hits the network, I start freezing.  It will say it copied 300-400MB, then kick in the network, then nautilus will be unresponsive, then everything frozen, then it will say it is copying 300-400 more (little network activity)... Just that continuous cycle.  I'm tempted to go get some :popcorn: but as this is happening at work it is more like ](*,) ... Any help would be greatly appreciated.

My current fstab has this:
server:/home/server/Desktop     /home/laptop/Desktop/server nfs     intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,tcp     0       0

The exports on the server has this:
/home/server/Desktop laptop(rw,sync,subtree_check)

I hope it is something stupid... please?
:D

---

### Post by hudsonl on 2010-08-19
> **hickwillie said:**
> Same problem here, the change in fstab settings didn't work for me.  I have the resource monitor on my panel and it is kinda weird.  Whenever I start the copy, it will go for about 300-400MB before it ever hits the network.  Once it hits the network, I start freezing.  It will say it copied 300-400MB, then kick in the network, then nautilus will be unresponsive, then everything frozen, then it will say it is copying 300-400 more (little network activity)... Just that continuous cycle.  I'm tempted to go get some :popcorn: but as this is happening at work it is more like ](*,) ... Any help would be greatly appreciated.

My current fstab has this:
server:/home/server/Desktop     /home/laptop/Desktop/server nfs     intr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,tcp     0       0

The exports on the server has this:
/home/server/Desktop laptop(rw,sync,subtree_check)

I hope it is something stupid... please?
:D


I would try changing in **fstab **rsize and wsize to 4096 and the async to **sync**

---

### Post by mcpish on 2010-08-27
> **hudsonl said:**
> I would try changing in **fstab **rsize and wsize to 4096 and the async to **sync**

Thank you, Thank you, that did it.  It fixed my problem.  I was having this problem too for the past few months and finally put 1+1 together and thought it might have something to do with upgrading to 10.04.  I had thought that my Router was breaking down and I was about to replace it.  But that "sync" option in my fstab seems to have done the trick.  None of that annoying lockup when copying over large video files from one machine to another via NFS :D

---

### Post by hudsonl on 2010-09-01
> **mcpish said:**
> Thank you, Thank you, that did it.  It fixed my problem.  I was having this problem too for the past few months and finally put 1+1 together and thought it might have something to do with upgrading to 10.04.  I had thought that my Router was breaking down and I was about to replace it.  But that "sync" option in my fstab seems to have done the trick.  None of that annoying lockup when copying over large video files from one machine to another via NFS :D


Your welcome !!  :)

Glad it worked ....

---

