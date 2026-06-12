---
title: "Memory Creep + Flush processes"
date: 2010-10-22
forum: General Help
---

### Post by rMatey on 2010-10-22
Well, I've upgraded to Lucid 64-bit and noticed a lot of strange activity in my System Monitor and memory usage.  The Processes list a lot of Flush 7-x's, which don't seem to terminate - ever.  I got one Flush 8:0, but doesn't seem to have any file or memory usage.
  Got rid of the Flush 7:x's by removing the Shotwell program.  My memory usage has lowered considerably, and a side benefit seems to be a really faster boot.
  What I did after removing the Shotwell program was to reboot twice without logging in - and the flush 7:xs ( about eight or more) just disappeared.
  Any ideas????  I'm considering going back to 10.04 where I did not notice this weird behavior.
  Oh, my old celeron laptop with 2 GB memory doesn't have that problem, but uses 32-bit 10.10  The desktop I built has 4 Gb

---

### Post by rMatey on 2010-10-22
Forget it!  Saw the messages about dirty memory again.  It has something to do with the disk writes, not with the cache for ISPs, internet, browser or anything else.  The memory creep only started with 10.10  I also converted to EXT4 for the 1TB extra disk that was already in there.  The disk checks clean.
  Sorry, I can't play anymore.  Going back to 10.04 LTS which seemed to work. Wish I never wanted more and settled for a  lot less.
  10.04 started faster, didn't print lines saying dirty disk writes or whatever.  It just worked.  Going back to what I had, using my backup.

---

