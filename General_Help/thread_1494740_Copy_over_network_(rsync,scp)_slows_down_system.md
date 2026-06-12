---
title: "Copy over network (rsync,scp) slows down system"
date: 2010-05-27
forum: General Help
---

### Post by fnokke on 2010-05-27
I have a newly installed Dell Optiplex 755 with Ubuntu 10.04 (64-bit) and I am having serious issues with network copying. Whenever I start rsync och scp with larger amounts of data my system becomes practically unresponsive (all types of apps grey out) until those processes are completed. Cpu stays at below 10% and I have lots of free memory and such ... any suggestions?

---

### Post by huit on 2011-05-17
I have this same issue copying ~1TB locally with rsync (to external hard drive).  The system becomes largely unresponsive (even typing in terminal misses keystrokes) soon into the transfer despite not appearing to consume all CPU/RAM (from top command).

edit: running Ubuntu 10.04 (64-bit) also

---

### Post by HermanAB on 2011-05-17
Howdy,

The trick is to use the rsync BW option so it doesn't bog down your system.  Read the rsync man page for details.

---

### Post by huit on 2011-05-17
thx HermanAB, I was just about to edit my post again and say it looks like i had a man-look at the top output. My RAM is full (Mem:   3799828k total,  3705292k used, 94536k free), it isn't using swap - the -W option looks like the key for me.

EDIT: Yep, did the trick! Didn't try the -B option though...

---

