---
title: "Issue a specific shutdown command"
date: 2009-11-22
forum: General Help
---

### Post by MartyBuntu on 2009-11-22
Okay, so if I have something running on my computer (Karmic) and I know the process roughly finishes before 11:00AM and I want to shut my computer down after the process ends, I can do this:

**sudo shutdown -h 11:00 "end of process"**


What is a command I can issue through the terminal to shutdown a specific running process at a given time?

I would like my video capture to end without me attending to it.

---

### Post by SGAZ on 2009-11-22
The time parameter in the SHUTDOWN command is a countdown timer so you could set (guess) how long until your work is finished and proceed using that command.

If you want it to run at a specific hour:Minute (like 11 in the morning) then you might try the 'at' command. Some examples: [http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html]("http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html")

---

### Post by MartyBuntu on 2009-11-22
Okay, but I don't want to shut down the entire computer. That was just an example. I just want to terminate a specific running process at a time I determine through the terminal.

---

### Post by SGAZ on 2009-11-22
Once the process is running you can use "ps aux" to find the process ID then use the AT command to kill that process specifically at the specified time.

I just tried it using gedit as the application to "kill" on schedule and it works fine:
[INDENT]sgaz@sgaz-desktop:~$* **at 8:31pm***
warning: commands will be executed using /bin/sh
at> ***kill pid###***
at> <EOT>
job 8 at Sun Nov 22 20:31:00 2009[/INDENT]

---

### Post by MartyBuntu on 2009-11-23
Thanks very much. I'll try this out.

---

