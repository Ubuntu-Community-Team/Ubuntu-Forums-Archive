---
title: "Memory Leak"
date: 2009-11-19
forum: General Help
---

### Post by dethmeggle on 2009-11-19
Just went through and dl'ed the updates a couple days ago (I'm using 8.04.3), and since then I've been having an atrocious memory leak. Right now RAM's up 68%, and Firefox is all I'm running. I can't figure out which program is responsible. 

Is anyone else having this problem?

---

### Post by XCan on 2009-11-19
What does the system monitor or "top" say about which processes are consuming the RAM?

---

### Post by muteXe on 2009-11-19
And does your RAM usage keep going up if you close firefox?

---

### Post by dethmeggle on 2009-11-19
Firefox is running on 289 MiB, and system monitor 4.6 MiB.

It goes down a little when I close out Firefox entirely, but not by a tremendous amount. Also noticing usage on my swap drive.

---

### Post by AnthonyI on 2009-11-24
I'm having the same problem in Ubuntu 9.10

nautilus (and even more, Xorg) are slowly sucking up my memory.

After a killall on nautilus, top reported almost 900mbs of memory (and growing) from Xorg.

Everything gets fine after awhile after restarting the computer, but eventually those two programs begin eating up at my memory again.

There is a topic on launchpad about this subject, for anyone reading this: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/484521](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/484521)

---

