---
title: "GUI login fail with NFS /home mounted"
date: 2011-04-27
forum: General Help
---

### Post by wkuhns on 2011-04-27
I had a bizarre problem with my Ubuntu 10.10 desktop after a thunderstorm - I'd like so help figuring out what happened. Here's the details:

Desktop has /home mounted from an older Kubuntu server - kernel version 2.6.24-19. Server has pretty bulletproof UPS.

We had a power glitch and the desktop rebooted. The server stayed up. After the desktop came back up, I went to log in via the GUI and got just a blank screen with a mouse cursor.

I logged into a console (ctl-alt-F2) as root. The /home directory was properly mounted. I tried logging in as myself at a console. No problems, no errors.

Hmm.... Corrupted configuration files for GUI tasks in my home directory? I rebooted and unmounted the /home directory via a root console. I have a skeletal /home on the local hard disk. I tried a GUI login as myself - success! Must be a bad config file on my server /home directory, right?

I moved all files (including hidden files) in my server home directory to a new subdirectory and tried the GUI login - no luck - same blank screen. I restart nfs-kernel-server task on the server and try again. No luck. Tried logging in as a different user - no luck.

I check EVERYTHING about the NFS mounted /home directory. Correct permissions, mount options, can create and delete files - everything looks fine.

I fire up a different computer that mounts /home from the server. I can log in, but lots of problems. Programs hang while starting, everything is sluggish.

Reboot server - everything is fine.

So - what happened? I've never seen this and I can't work out a reasonable explanation. Early on there were some nfs related lockd errors in the desktop logfile, but later failures didn't result in any logged errors.

This is more a curiosity than an emergency, but any ideas would be welcome.

---

