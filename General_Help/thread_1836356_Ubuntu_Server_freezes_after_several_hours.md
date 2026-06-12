---
title: "Ubuntu Server freezes after several hours"
date: 2011-08-31
forum: General Help
---

### Post by thebrandon on 2011-08-31
So I just recently reinstalled ubuntu server 11.04 after I messed up my previous install and left my computer sitting unused for a bit.  Install went great but now after eight hours or so it will freeze up and I cant access it via ssh.  When I try to reboot it wont even boot up all the way and I have to disconnect the power cord and reconnect it to get it to boot back up properly.  I dont even know where to start to look for a log file as to what is going wrong.  I can tell say its not being really used I have only installed ps3 media server which wasnt running and I installed ampache but again neither is being used yet.  It simply hangs while sitting idle.

---

### Post by deserthowler on 2011-08-31
I had a similar problem with a box running Ubuntu 10.04 Desktop.  I found it was a problem with a memory stick.

Earl

---

### Post by thebrandon on 2011-08-31
So you think I could have bad ram?  How can I tell?

---

### Post by dino99 on 2011-08-31
watch your logs to know about that issue. Htop can show you which process is eating ressources.

---

### Post by deserthowler on 2011-08-31
> **thebrandon said:**
> So you think I could have bad ram?  How can I tell?

I had 4 mem sticks of 512.  I pulled 2 and tested and had the same problem.  Then I pulled them and put in the other 2 and didn't.  I got 2 new ones.  No more problems.

Run Mem test from grub to see if that works.  Sometimes that will give a false negative reading though.  Might give a place to start though.

Earl

---

### Post by thebrandon on 2011-09-06
Well you were right, i dug up another stick and swapped it out with one of the ones I had in there and it has been running ever since.  Thanks for the help!

---

