---
title: "why does iotop not work after installing pae"
date: 2011-12-01
forum: General Help
---

### Post by wxuyec on 2011-12-01
I installed the pae for my ubuntu10.04 kernel of 2.6.35-31.
after restart, when I run "iotop", I got the errors:
$ iotop 
Traceback (most recent call last):
  File "/usr/bin/iotop", line 16, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 547, in main
    main_loop()
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 537, in <lambda>
    main_loop = lambda: run_iotop(options)
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 452, in run_iotop
    return curses.wrapper(run_iotop_window, options)
  File "/usr/lib/python2.6/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
  File "/usr/lib/pymodules/python2.6/iotop/ui.py", line 444, in run_iotop_window
    process_list = ProcessList(taskstats_connection, options)
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 338, in __init__
    self.update_process_counts()
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 394, in update_process_counts
    stats = self.taskstats_connection.get_single_task_stats(thread)
  File "/usr/lib/pymodules/python2.6/iotop/data.py", line 125, in get_single_task_stats
    reply = self.connection.recv()
  File "/usr/lib/pymodules/python2.6/iotop/netlink.py", line 229, in recv
    raise err
OSError: Netlink error: not permitted operation (1)

---

### Post by Toz on 2011-12-03
> **wxuyec said:**
> 
OSError: Netlink error: [COLOR="Red"]not permitted operation[/COLOR] (1)

If you're running iotop as a regular user, try:
```
sudo iotop
```

---

### Post by dcstar on 2011-12-04
> **wxuyec said:**
> I installed the pae for my ubuntu10.04 kernel of 2.6.35-31.
........

If you have less than 4GB RAM then using a PAE kernel is pointless, if you have 4GB or more then you may also need to adjust some BIOS settings to allow PAE to work correctly with your hardware.

---

