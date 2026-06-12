---
title: "Disc being accessed continuously, WHY??"
date: 2011-11-01
forum: General Help
---

### Post by producer on 2011-11-01
It's curious.  My disk is constantly going Bbbrrrrrrruup, Bbbrrrrrrruup, and the little heads are flying around quite audibly, but I don't know what process could be doing that, or why.   The disk is only 76% full and I disables anything I had running that might create such activity.  It just seems to continue whether I'm online of off.  It's sort of rhythmic, every second or so a new Bbbrrrrrrruup, but it's not exactly uniform.   Does anyone have any ideas.  I'm running Ubuntu 10.10 and Gnome 2.32.0.

---

### Post by Perryg on 2011-11-01
Run iotop and see what is r/w to the disk.  It has been around for some time.
Here is the one that is affecting me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560)

---

### Post by producer on 2011-11-01
I installed iotop and ran itt and it produced a bunch of errors, no real output.
-------------------
Traceback (most recent call last):
  File "/usr/bin/iotop", line 16, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 547, in main
    main_loop()
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 537, in <lambda>
    main_loop = lambda: run_iotop(options)
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 452, in run_iotop
    return curses.wrapper(run_iotop_window, options)
  File "/usr/lib/python2.6/curses/wrapper.py", line 43, in wrapper
    return func(stdscr, *args, **kwds)
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 444, in run_iotop_window
    process_list = ProcessList(taskstats_connection, options)
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 348, in __init__
    self.update_process_counts()
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 404, in update_process_counts
    stats = self.taskstats_connection.get_single_task_stats(thread)
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 135, in get_single_task_stats
    reply = self.connection.recv()
  File "/usr/lib/pymodules/python2.6/iotop/netlink.py", line 229, in recv
    raise err
OSError: Netlink error: Operation not permitted (1)
---------------------------

---

### Post by JRV on 2011-11-01
Are you short of RAM and is it using swap to try to make up for it?

This sounds like a virtual bind.

---

### Post by Perryg on 2011-11-01
try this:
sudo iotop -o
Then watch to see what it popping in and out.

---

### Post by producer on 2011-11-01
Nothing seems to be there except claws mail and that is infrequent.  I think only when it fetches mail. Otherwise nothing is listed.  One listing went in and out very quickly when I first started the iotop -o ... couldn't read it fast enough.  The disk seems to have quietened down now however. and there is no red access light except once in a while, but I know what that is.
I have 2 Gigs of memory.

---

### Post by producer on 2011-11-01
OK it's fine now.

---

