---
title: "&quot;Preload&quot; anyone using it ?"
date: 2012-04-20
forum: General Help
---

### Post by jerrrys on 2012-04-20
I have been installing it since 8.04, but wonder if anyone else finds this package of any use.
Don't seem to hear much about it anymore.

For those not familiar with this package; its in the software center.  Description:

preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

---

### Post by dino99 on 2012-04-20
you miss the most important:  that preload is a daemon that runs with root priviledges

so be aware ):P

then its a puter race with yourself :guitar:

---

### Post by jerrrys on 2012-04-20
be aware of what?

---

### Post by CharlesA on 2012-04-20
> **jerrrys said:**
> be aware of what?
I'm not sure what dino99 is trying to get at.

It runs on a single machine and doesn't listen on the external interface, right?

---

### Post by raja.genupula on 2012-04-20
[http://ubuntuforums.org/showthread.php?t=707743&page=2](http://ubuntuforums.org/showthread.php?t=707743&page=2)

---

### Post by jerrrys on 2012-04-20
Hi CharlesA: I assume so

Raja: Preload was popular in 2008.  Thanks for the link

---

### Post by Paqman on 2012-04-20
> **CharlesA said:**
> I'm not sure what dino99 is trying to get at.


He's just implying that every extra line of code that runs as root is a theoretical risk. A very, very theoretical one if you ask me.

Preload is all good. Should be installed by default.

---

### Post by jerrrys on 2012-04-20
readahead is installed by default

---

### Post by Derek Karpinski on 2012-04-20
I use it, and I find it useful.  It will increase boot time a bit, but having Firefox start instantly after a cold boot is nice.

---

### Post by LewisTM on 2012-04-20
Preload is as useful as ever. It significantly increases the startup speed of most apps on all of my machines. The daemon uses a bit of RAM but hey, why not put that free RAM to good use?
There's really no reason not to install it, it should be default IMO.

ureadahead fills another role, it reads system startup files ahead of time for faster boot. It has little impact at the post-login stage.

Cheers!

---

### Post by jerrrys on 2012-04-21
bump

---

### Post by ickefes on 2012-08-24
I use it in Ubuntu 12.04. My low end ASUS K53SV's disk drive's ability to start reading files is really slow and if I understand  correctly that's because it saves a lot of power. I can get up to 7 hours of battery use but programs load severely slow and Preload keeps my ADHD to an acceptable level.

---

### Post by jerrrys on 2012-08-25
And look what pops up on radar.

This is an old thread.

R.I.P.

---

