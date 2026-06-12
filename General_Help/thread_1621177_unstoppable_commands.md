---
title: "unstoppable commands"
date: 2010-11-13
forum: General Help
---

### Post by buchs on 2010-11-13
I am at 10.10 Ubuntu for a few months now and I have a problem that seems to have arisen about the time of the upgrade.  Certain commands that I issue from a shell or other means will not execute (no output) and are unable to be cancelled, killed, blasted or otherwise destroyed, except by reboot.  Typically these involve devices (mount, unmount, dd) and my DVD-drive is often the culprit.  

Following a boot/reboot, I seem to get 1 read of a CD/DVD.  It will automount and I can umount it.  But, if I change the media, or even remove and re-insert the same media, a mount will not complete.  It will not automount nor will a manual mount work.  The attemped manual mount will never return and I cannot get it to stop.

I have tried to stop with Control-C or Control-Z in the terminal.  From another terminal I find the process ID and have tried kill and sudo kill -9 to no avail.  I have tried to kill the running terminal session (File->Close, window close).  Even if I succeed in killing the terminal session, the command I entered is still there on the list of processes.

I command is not taking up any CPU resources.  No other process will be taking more than 1% of the cpu.  I can close all the applications and nothing changes.  

This experience totally defies my prior Linux and Unix experience.  kill -9 always did its job.  kill is running /bin/kill, an ELF file last modified in 2009.  Kill works in all other occasions though sometimes it may be a bit slow.

Can anyone share any insights on this that might help me prior to a wipe and fresh install?

Thank you.

---

### Post by dcstar on 2010-11-13
> **buchs said:**
> I am at 10.10 Ubuntu for a few months now and I have a problem that seems to have arisen about the time of the upgrade.  Certain commands that I issue from a shell or other means will not execute (no output) and are unable to be cancelled, killed, blasted or otherwise destroyed, except by reboot.  Typically these involve devices (mount, unmount, dd) and my DVD-drive is often the culprit.  

Following a boot/reboot, I seem to get 1 read of a CD/DVD.  It will automount and I can umount it.  But, if I change the media, or even remove and re-insert the same media, a mount will not complete.  It will not automount nor will a manual mount work.  The attemped manual mount will never return and I cannot get it to stop.
..........
Can anyone share any insights on this that might help me prior to a wipe and fresh install?

Thank you.

System calls to faulty hardware cannot be killed, only the process that initiated the call.

If you have faulty hardware - or the system has a problem with it - you have to wait for the various system timeouts built into the kernel and there is precious little you can do about it.

The ATA standard has a timeout of 30 seconds (IIRC), so if you have a faulty DVD drive then for each low-level command the system sends to it, it will wait 30 seconds before retrying (which it may do multiple times before giving up).

Use a 10.10 Live USB to thoroughly test your hardware and determine if things behave ok compared to your install.

---

### Post by buchs on 2010-11-14
David,

Thanks for the suggestions.

First, I would clarify:
> **dcstar said:**
> System calls to faulty hardware cannot be killed, only the process that initiated the call.

What I am saying is that I cannot kill the process.  It continues to be listed on the ps listing, showing the mount, umount or dd command.  It doesn't matter if I kill all its predecessor processes, either.  Those processes go away but the process with the given command persists, listed as a process with ps.

> Use a 10.10 Live USB to thoroughly test your hardware and determine if things behave ok compared to your install.

I did indeed try this and found that all was working fine.  If there are any suggestions short of re-install, I would love to learn of those.  

Maybe someone also knows the tricks to doing a reinstall without formatting a partition?

Kevin

---

### Post by buchs on 2011-01-24
This issue was resolve by reinstalling Ubuntu.

---

