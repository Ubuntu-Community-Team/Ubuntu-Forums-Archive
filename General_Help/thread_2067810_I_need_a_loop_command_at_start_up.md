---
title: "I need a loop command at start up"
date: 2012-10-07
forum: General Help
---

### Post by nahuel_89p on 2012-10-07
Hi, i need to run this command at start-up,

> echo level 7 | sudo tee /proc/acpi/ibm/fan

This turns on the fan of my laptop, but only for a few seconds. Its just a burst.
I need this because my laptop overheats making the system crash, so i thought it would be good to automatize the fan.

I need a way to make this command auto-execute every 30 seconds or so.
Any idea?

Thanks in advance.

---

### Post by cipherboy_loc on 2012-10-07
Take a look at [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

I would write a script (place it in like /usr/local/bin, chmod +x) that makes sure it is root, then runs enters a infinite loop to run your command, sleep for 25 seconds (to be safe), then repeats. 

Write a upstart script to start this and background it (ie, /path/to/script &), and kill it (either track pid or use killall) on stop. If you need more help, just ask.


Thanks,
Cipherboy

---

