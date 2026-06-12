---
title: "Want to strip desktop system to server system."
date: 2006-02-19
forum: General Help
---

### Post by sledgehbk on 2006-02-19
Hi everyone. I'm new. :)

I've been playing with Ubuntu for about three months now. I installed it on an older box I had initially, but over the course of playing with it, I installed Ubuntu on my main work machine. When I made that decision, my older box became a server for my little personal blog, and for streaming music. I set ubuntu to log in to a neutered user account automatically when it boots, and disconnected the monitor.

Well, I have searched for help, but my efforts have come up short. I want to remove any and all GUI's that Ubuntu installed, and have the machine's hardware not have to worry about loading any of that stuff, saving cycles for whatever I am using the server to play with.

Okay, rambled long enough. How do I go from Ubuntu Desktop -> Ubuntu Server without a lot of hassle and without deleting the configuration I have for set for it serverwise?

Thanks in advance!

---

### Post by alamba on 2006-02-19
You could start with uninstalling the packages for gnome and/or kde. Not sure how it'll effect your setting though.

A

---

### Post by nanotube on 2006-02-19
well, the easiest thing to do would be just to stop gdm from loading on startup, so that it throws you into a plain black terminal.

to do that, just run 
```
sudo update-rc.d -f gdm remove
```
from a terminal, and that will do it.

now, if you also want to free up some disk space from having X and gnome and whatnot, then you would have to uninstall a bunch of packages. but unless you are /really/ low on diskspace, there is no point. just stopping it from running automatically will free up the system resources for you.

---

### Post by Ocxic on 2006-02-19
unless your upposed to the idea, a freash server install would work.
you could also try: sudo dpkg-remove ubuntu-desktop

---

### Post by alamba on 2006-02-19
Perhaps changing the runlevel would be a better option? 

A

---

### Post by sledgehbk on 2006-02-19
Wow, so quick with the help, you guys are really sharp!

(Thanks for treating this noob with a little respect, I appreciate it!)

Some good suggestions, but I think I like nanotube's idea best. Disk space is not at a premium (I plan on adding a disk later).

However, this brings me to another hurdle. I used a program built into gnome (can't remember what it was called, not at an ubuntu workstation atm) that would log in automatically and start all the services (Web, SSH, FTP, SMTP). Will this still happen when it just stays at a black-screen terminal at boot?

Again, forgive my ignorance.

---

### Post by nanotube on 2006-02-19
well, i am not sure what program you used... but the easiest way to check it is to turn off gdm, reboot, and then see if the services are running. :)

i suspect that whatever you used probably just made the services start up at boot. there is a very nice package called "sysv-rc-conf" that lets you see what services you have set to start up at which runlevels. (or, of course, you can just go and see what symlinks you have in /etc/rcX.d directories (where X is a number 0-6). default runlevel is 2, so see what you have in /etc/rc2.d

btw, if you turn off gdm, but want to start it later manually, you issue command:
```
sudo /etc/init.d/gdm start
```

---

