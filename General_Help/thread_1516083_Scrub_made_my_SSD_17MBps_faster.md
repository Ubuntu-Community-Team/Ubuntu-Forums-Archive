---
title: "Scrub made my SSD 17MBps faster"
date: 2010-06-23
forum: General Help
---

### Post by 98cwitr on 2010-06-23
Against my better judgement (since it's an MLC device) I ran scrub on the free space of my SSD, which writes dummy data to all the remaining space on the drive and then deletes it. After I ran it, I went from 250MB read to 267MB (the original benchmark when I first got the drive). Im pretty stoked, but I wonder how much life I just depleted from the drive by writing all that data to it :?

---

### Post by Rhubarb on 2010-06-23
It's just the 1 write, so it's fine to do.
I haven't ever ran into flash writing issues ever, even when I do run a journalling file system.
A bit of extra speed is always nice :-)

The next version of ubuntu 10.10 will have a newer kernel which supports the new trim command for SSDs.

---

### Post by 98cwitr on 2010-06-23
I have already installed 2.6.34 and enabled TRIM...still got 250MB before running scrub.

---

