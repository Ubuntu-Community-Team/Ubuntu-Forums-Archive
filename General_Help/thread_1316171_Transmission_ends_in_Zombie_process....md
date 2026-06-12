---
title: "Transmission ends in Zombie process..."
date: 2009-11-05
forum: General Help
---

### Post by jwsalaz on 2009-11-05
I use Transmission for torrents.  After a fresh install of Karmic, I connect to peers (3 or more), and all of a sudden the Transmission dialog grays out.

I go to check the System monitor, and lo and behold, my CPU is being eaten alive by Transmission as a zombie process.

Any ideas?  And how can I get this committed to Launchpad?

---

### Post by Harpalus on 2009-11-06
Same problem here. It stops responding altogether, and nothing can kill the process. The only option for me is apparently to restart, as even logging in and out will not stop the process, and neither will kill -9 <PID>.

---

### Post by Giblet5 on 2009-11-06
Transmission doesn't work as well as almost ANY other torrent application.

Bleeding edge. I wonder why they call it that.

---

### Post by jwsalaz on 2009-11-06
OK, it's not just me.  I'm glad to know that.  Thought I was going crazy.

---

### Post by jwsalaz on 2009-11-07
I am testing on x64 now, and Transmission does NOT zombie out.  Something on the x86 upsteam must be doing it.

---

### Post by RedClairefield on 2009-12-25
This is happening to me and I'm hoping there's a way to work around this because it's not really effective to torrent files on my windows machine and carry the files over here with a flash drive.

Quick edit: It's been a zombie for a good five to ten minutes and now it is back to normal. I wonder what is going on.

---

### Post by _bl on 2010-05-19
on 10.4 Transmission like a zombie too (((
AMD64 and i386

---

### Post by gator on 2010-09-18
Same problem on meerkat. ktorrent does the same thing. Processes cannot be killed - needs restarting. This is on x86.
Ive tried the pae kernel with the same results - Transmission locks up, system monitor shows futex_wait_queue_me

---

### Post by gator on 2010-09-29
reinstalled with x64 - latest CD and torrents with transmission work as expected.

---

### Post by Yellobes on 2010-11-21
[HTML]<p> 2 <sup>nd</sup> ed, Transmission sucks. What should it be replaced by? </p>[/HTML]

---

### Post by ziggrat on 2010-12-07
Same thing happened to me on Ubuntu 10.10. I think i know the reason, since transmission was working fine before i tried to download a torrent for a 6 gig file. I think the file size over 5 gig is making transmission, a zombie process. Once i removed that torrent and deleted the file, its working fine. I'm guessing its a file system issue.

---

