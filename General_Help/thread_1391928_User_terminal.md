---
title: "User terminal?"
date: 2010-01-27
forum: General Help
---

### Post by pepsifx357 on 2010-01-27
Is there a terminal I can open up that will show me the background system working.  Something that I can put on my second monitor that will show me a readout of all the things I click on, run, and do?

---

### Post by pepsifx357 on 2010-01-27
Bump

---

### Post by t4thfavor on 2010-01-27
in the terminal, you could type.

```

top

```

---

### Post by hhlp on 2010-01-27
you can use also 

htop

---

### Post by pepsifx357 on 2010-01-27
htop is kinda cool.  So theres not a terminal and spits out active processes? Kinda like when you run a program from the terminal and you can see what commands it runs.

---

### Post by mcduck on 2010-01-27
No, there's no such thing. Most of the graphical apps don't actually run any commands (at least not in that sense).

If you want to monitor what's going on in your system you can follow the log files located in /var/log.

For example pop open a terminal and run "tail -f /var/log/sysylog" ("tail -f" will read the last lines of a text file and then keeps on updating as the log file gets updated. Press Ctrl-C when you want to stop it). You'll see lots of information about processes running in the background (like all kinds f network-related stuff, how devices are recognized and assigned to drivers when you plug them in and so on). Feel free to check the other log files as well.

---

### Post by pepsifx357 on 2010-01-27
Thanks mcduck, by the way, is the code you posted correct?  I got a:

tail: cannot open `/var/log/sysylog' for reading: No such file or directory
tail: no files remaini

---

### Post by hhlp on 2010-01-27
```
tail -f /var/log/syslog
```

---

### Post by pepsifx357 on 2010-01-27
It works, thanks!

---

