---
title: "automatic shutdown"
date: 2010-02-18
forum: General Help
---

### Post by karmicgaz on 2010-02-18
I like to periodically run "bleachbit" but I would like to set it to run, then close and shut the computer down. Can anyone tell me a command to make that happen?

---

### Post by MinimalBin on 2010-02-18
```
sudo shutdown -h now
```

** Use /etc/sudoers to allow execution without a password.

---

### Post by Ordes on 2010-02-18
sudo shutdown -h +X
sudo shutdown -h xx:yy

1) +x >> minutes to shutdown  (e.g +60 )
2) xx:yy >> time to shutdown (24:00 hrs; e.g. 15:35)

---

### Post by karmicgaz on 2010-02-19
Forgive me, I didn't explain it that well, I want a command I can type BEFORE I run bleachbit so I can set it in motion safe in the knowledge it will shut down when finished. Obviously the time command will work but it's a guestimation on completion time, so the command I want will run bleachbit then shutdown the computer when completed.

---

### Post by troyatlarge on 2010-12-16
> **karmicgaz said:**
> Forgive me, I didn't explain it that well, I want a command I can type BEFORE I run bleachbit so I can set it in motion safe in the knowledge it will shut down when finished. Obviously the time command will work but it's a guestimation on completion time, so the command I want will run bleachbit then shutdown the computer when completed.  There is a way to do such a thing and its not very difficult (I think), however, I will have to look at it later today and get back to you (make sure it runs right and all).

---

### Post by rubylaser on 2010-12-16
You could just write a simple bash script to run bleachbit via the cli and then run the shutdown command after that.  Something like this...

```
#! /bin/bash
bleachbit --delete firefox.vacuum other options here... && /sbin/shutdown -h now
```

Then add it to your crontab
```
0 3 * * 5 /root/scripts/bleachbit_cleanup.sh
```

That's how I'd do it.  Hope that helps.

---

