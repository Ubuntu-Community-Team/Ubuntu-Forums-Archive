---
title: "I want to be the boss: tracker/locate/sched keep sending me for coffee"
date: 2009-07-24
forum: General Help
---

### Post by zoubidoo on 2009-07-24
There are a number of situations where my OS (Ubuntu) decides the user doesn't count.  It does its own business and the user can go get coffee. The OS is sending me to get coffee??  Wait up!  Who's the boss???

When tracker starts indexing, my laptop becomes unusable, it hogs all the resources.  Do you think it would be polite enough to check whether I'm around and busy using the machine?  Nope.  It's just plain rude and stomps on the resources and the user can just go make some coffee.

Ditto for locate (locatedb), again while indexing it chews the disk and that cripples my machine.

I know about cron, I know about ps+kill.  So I could reschedule or kill the indexer, but that's not the point.  The machine is supposed to be user-friendly.

[B]The screensaver can tell if a user is present by mouse/keyboard activity. locate and tracker indexers should be polite and do the same.
[/B]
That brings me to the kernel cpu scheduler.  Has anyone noticed that copying a large file to a usb key causes other processes to struggle. It also happens with heavy disk usage (tracker/locatedb/etc). IO-intensive applications cripple the machine. (I think it's called [priority inversion]("http://en.wikipedia.org/wiki/Priority_inversion")).  When this happens it's not a multi-tasking machine any more.  It's just busy copying the file and I can go make coffee...again.  I understand that juggling process priorities is hard, especially when I/O is involved, but this problem has been going on for years.

**I/O usage should not bring a machine to its knees.**

Finally, nice is not nice.  renicing a process to give it a low priority simply doesn't make it low priority enough and it still interferes with normal activity.  Lowest priority tasks should check that the CPU has been free for say 15 minutes before starting.

The above are all situations where I am not the boss of my OS.

I just want to be the boss, is that too much to ask?
/rant

Z.

PS I have brought these issues up several times over the last 5 years (bug reports, kerneltrap, brainstorm) but despite reassurances they just don't seem to want to go away.  They make Ubuntu a less user-friendly OS.  If you agree with any of these issues please chime in, and if you have a bit of clout would you consider having a word in the right ear?

---

### Post by zoubidoo on 2009-07-24
Another example: adding a USB key.  The thumbnailer launches and the mouse no longer responds until it has finished.

On a 1.5GHz processor that's a bug!

Off for another coffee...

Really, I can't keep drinking all this coffee.  May be I should take up cigarettes.

Z.

---

