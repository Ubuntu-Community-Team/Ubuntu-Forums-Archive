---
title: "Logging top to a file daily"
date: 2012-05-29
forum: General Help
---

### Post by gregom on 2012-05-29
I am not very good in Linux and I need help in tracking down why my DVR server is crashing. I'm running 8.04 x64 server. My system has been running over two years almost perfectly with a weekly scheduled reboot. Just in the last few weeks it started crashing a few times a week. oom kill process is typically Mysqld, but sometimes its another process which is critical to my DVR system.

I've already ran memtest for several hours and it didn't detect any problems with the memory. I tried to install Munin but couldn't really figure out how to set it up and use it. 

I think i'd like to just do something simple like log top to a file. All I want is to have top write to a log file every 10 seconds or so and let that accumulate for a day, and then start a new log file. Is this a simple line I could add in crontab? I tried searching around the net but with my limited knowledge I couldn't find anything for my specific need. Any guidance would be appreciated.

---

### Post by dcstar on 2012-05-31
> **gregom said:**
> I am not very good in Linux and I need help in tracking down why my DVR server is crashing. I'm running 8.04 x64 server. My system has been running over two years almost perfectly with a weekly scheduled reboot. Just in the last few weeks it started crashing a few times a week.
.........

8.04 has been unsupported for years, so no software changes could have occurred to cause any problems.

If you have problems now your hardware is failing.

---

