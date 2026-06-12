---
title: "Firefox at Shutdown - a bit of a pain"
date: 2011-10-16
forum: General Help
---

### Post by Quarkrad on 2011-10-16
Running 10.10.  For some reason wife's PC is not shutting down every time.  Been running ubuntu for about 2 years and got in the habit of 'shutting down' and walking off but lately we find the PC has not switched off but still running.  The culprit is firefox - firefox.bin does not always close down.  A solution is to go into System monitor and kill the process but this seems to be going back to the bad old windoz days when you need to sit there to may sure the pc actually did turn off.  Ubuntu is starting to show a similar bad habit.  Would it be worth un-installing firefox and re-installing or is there something more fundamental at play?  (note.  I have a similar problem on my machine but is issue is with Thunderbird - at times have to manual kill).

---

### Post by bossbruin on 2011-10-16
I am having the same problem.  The only way to shutdown or restart firefox for that matter is through the system monitor.  Help would be appreciated.

---

### Post by Quarkrad on 2011-10-17
bump

---

### Post by Morbius1 on 2011-10-17
This seems to be a relatively new phenomenon. I'm running 10.04 and what I had to do was this:

In Firefox go to:
```
about:config
```In the "Filter" bar enter:
```
dom.ipc.plugins
```And toggle the following lines to false:
[B]dom.ipc.plugins.enabled.libflashplayer.so
dom.ipc.plugins.enabled.libnptest.so

[COLOR=Blue]EDIT:[/COLOR] [/B]Didn't have the reference when I originally posted so I'll add it now:
[http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins)

---

### Post by Quarkrad on 2011-10-23
Thanks - did the trick and still no issues.  Do you know of a similar solution for Thunderbird?  I'm running 10.10 and occasionally get this 'process not closed' problem.  Just built a 11.10 system for my mother-in-law and seen this 'Thunderbird still running' message (only once to be honest) on that.

---

