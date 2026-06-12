---
title: "sudo / crontab help"
date: 2009-11-05
forum: General Help
---

### Post by weirdbeardmt on 2009-11-05
Hi

Suspect this is a newbie type issue but I'm not sure what's going on. Perhaps you can help me understand.

I am using the program 'motion' to run some webcams from my box. To start it, I use

sudo motion

It starts up and runs, fine. If I try to run it without sudo, then I get

Cannot create process file /var/run/motion.pid

If I run motion from crontab -e it starts, but doesn't work... presumably with the same error as above. 

If I change crontab to execute 'sudo motion', then it all works... and doesn't prompt me for a password which is quite odd.

And what's really confusing, is this all worked (without sudo in the crontab) before I built and installed the latest version (whereas previously I'd just used apt-get to install motion).

So, my question is this: why, if crontab runs as sudo by default, do I need to execute the command sudo motion in it to get it to work?

Hope that's clear! :)

---

### Post by Giblet5 on 2009-11-05
sudo won't *keep* working from crontab...

Sudo has a timeout.

Try it: ```
sudo ls
sudo ls
```

How many times did you get asked for a password?

The way to do this is A) configure motion to put the pid file somewhere where you're allowed to write, or B) put the command in root's crontab ```
sudo crontab -e
```

---

### Post by weirdbeardmt on 2009-11-05
I realise now that my testing of crontab was the reason that crontab didn't ask me for a password. I bet if it ran now, now that sudo has timed out, it would ask for password.

> 
The way to do this is A) configure motion to put the pid file somewhere where you're allowed to write, or B) put the command in root's crontab ```
sudo crontab -e
```

This is what I have always used... i.e., it has always been set up in root's crontab. But it doesn't work...

---

### Post by weirdbeardmt on 2009-11-22
Thanks. Turns out it was a combination of the PID location not being writable and the owner of /dev/video* (i.e. the webcams) was root... so made the PID location writable and made the owner of the video devices the same as the group and now is all working.

---

