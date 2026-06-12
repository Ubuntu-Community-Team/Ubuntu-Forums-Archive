---
title: "X server not starting"
date: 2009-11-13
forum: General Help
---

### Post by yargmematey on 2009-11-13
I turned ctrl+alt+backspace back on, and when I used it my x didn't restart, and I was presented with a command line.  "Startx" threw an error ("No screens found").  Is there a solution?  I'm thinking about just reinstalling (as I just did the install and I wont really lose anything) but I feel like knowing how to fix stuff like this would help me later in life.

---

### Post by Giblet5 on 2009-11-13
> **yargmematey said:**
> I turned ctrl+alt+backspace back on, and when I used it my x didn't restart, and I was presented with a command line.  "Startx" threw an error ("No screens found").  Is there a solution?  I'm thinking about just reinstalling (as I just did the install and I wont really lose anything) but I feel like knowing how to fix stuff like this would help me later in life.

Try logging in and entering ```
sudo /etc/init.d/gdm restart
```

If you ever see this issue again, you can grab a copy of /var/log/Xorg.0.log via ```
sp /var/log/Xorg.0.log Xorg.log
sudo /etc/init.d/gdm restart
```

Then open the Xorg.log file in your home directory and see if you can figure out why Xorg fails to restart on its own.

---

### Post by yargmematey on 2009-11-15
The first command did not work, with ubuntu telling me that

"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm restart

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart(8) utility, e.g. restart gdm gdm start/running, process 2146"

The second command returns:

"sp: command not found"

Thanks, though.

---

