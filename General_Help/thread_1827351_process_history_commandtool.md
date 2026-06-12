---
title: "process history command/tool?"
date: 2011-08-17
forum: General Help
---

### Post by aeronutt on 2011-08-17
Is there any tool or command that will record the history of every process (or command) running on a system over a time window (say, a few minutes for example)?

---

### Post by seawolf167 on 2011-08-18
Like writing the current processes into a file?

```
ps -ef > some_file
```

or a specific process?

```
ps -ef | grep -i process_name > some_file
```

or to monitor processes?

```
sudo apt-get htop
htop
```

---

### Post by aeronutt on 2011-08-18
Fair question!  I'll describe what I really want.:)  I'd like to capture the command that gets executed when I click on a GUI button, so that I could replicate that command on CL. But, obviously, some commands only take microseconds to execute, so using htop, ps, etc, are hard to use to capture that command. So...ideally...I'm looking for a tool (or script) to capture every command or process excuted over a small window of time (30 second window would be fine, for example, probably even 10 seconds.) Or, is there a better way to know what a GUI is doing?

---

### Post by aeronutt on 2011-08-20
Anyone have any ideas? Seems this would be a useful tool.

---

### Post by Frogs Hair on 2011-08-20
There are some real time monitoring tools / commands at the link , but I don't know about a logging tool .  I think storing that information could use a lot of space in a short time .[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

