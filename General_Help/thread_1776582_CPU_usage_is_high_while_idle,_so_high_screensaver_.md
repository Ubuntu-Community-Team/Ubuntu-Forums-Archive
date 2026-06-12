---
title: "CPU usage is high while idle, so high screensaver getting stuck"
date: 2011-06-06
forum: General Help
---

### Post by wbuntu on 2011-06-06
load average: 0.24, 1.65, 4.23
the 4.23 is while idling.
How can I check what is causing this? without sshing in to it while its idle
Thanks.

---

### Post by Toz on 2011-06-06
Open a terminal window and type/paste in the following code:```
while true; do ps -eo pcpu,pid,cmd | grep -v "%CPU" | sort -nr | head >> ps.log; echo "==========" >> ps.log; sleep 15s; done
```

Feel free to change the **sleep 15s** to some other value (15s = 15 seconds). Basically, this will print the top 10 cpu-intensive processes to a file called ps.log every **sleep 15s** (or whatever you change it to) separated by ========= for readability.

Press the enter key to start the recording, and initiate the screen-saver. When the screensaver acts up, review the contents of ps.log to see what was consuming the cpu cycles.

---

