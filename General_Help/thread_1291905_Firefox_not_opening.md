---
title: "Firefox not opening"
date: 2009-10-15
forum: General Help
---

### Post by nipunreddevil on 2009-10-15
Just now firefox stopped working on my system.When i click on the link it seems it will open up but then firefox doesnt open

---

### Post by DeMus on 2009-10-15
> **nipunreddevil said:**
> Just now firefox stopped working on my system.When i click on the link it seems it will open up but then firefox doesnt open

Look in your system monitor to see if there is still a copy of FF running. If so, kill it.

---

### Post by vipulkelkar on 2009-10-15
open the terminal
give the following commands

ps -e

Look for any firefox process running..note the pid

kill pid(the pid of firefox)

---

### Post by nipunreddevil on 2009-10-15
No firefox process is running

---

### Post by vipulkelkar on 2009-10-15
reboot the system and try running it..else check this out 

[http://www.linuxforums.org/forum/ubuntu-help/111566-firefox-not-responding.html](http://www.linuxforums.org/forum/ubuntu-help/111566-firefox-not-responding.html)

check the last post

---

### Post by masux594 on 2009-10-15
trying to open firefox from a terminal and see if there's some error message?

Sysc, A

---

### Post by nipunreddevil on 2009-10-15
A restart worked.Dont know why ,but after restart  when i again started firefox ,it started as if it was a first run

---

