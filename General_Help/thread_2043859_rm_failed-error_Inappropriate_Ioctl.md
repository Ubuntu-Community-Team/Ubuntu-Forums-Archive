---
title: "rm failed-error: Inappropriate Ioctl"
date: 2012-08-17
forum: General Help
---

### Post by hangle on 2012-08-17
My system indicates that I have exhausted all my disk space.  There are two
large files causing this problem (resource0 and resource0_wc).   Attempts
to delete these file, as root user, fails with the message:
               Inappropriate ioctl for device while reading flags on resourc0

From time to time I have had a similar problem with the file ~/.xsession-errors.
It has consumed all my disk space.   I have deleted it,  rebooted the system
in 'repair mode', and restored the available disk space to 83% available.
The problem with .xsession-error occurred yesterday.  In a attempt to correct the
problem before rebooting, i took the following steps to prevent this file from
ever expanding:
              rm  .xsession-errrors
              touch .xsession-errors
              sudo chattr +i .xsession-errors

I am beginning to suspect that I made the problem worse, perhaps forcing
the applications that writes to .xsession-errors to write elsewhere, like to
resource0 and resource0_wc. 

i am worried about rebooting without removing resource0 and resource0_wc.
I am afraid the system will not have any disk space to recover.  On the other
hand I cannot do any work without diskspace.  Deleting other files will not
work until the system reboots.  It seems like a lose-lose situation.  Any
suggestions will be appreciated.

Thanks,
Hugh Angle

---

### Post by lukeiamyourfather on 2012-08-17
I'd try booting with a live disc and removing the two large files. While you're at it make a backup of stuff you haven't yet just in case. Reversing the attribute (chattr -i) should fix the issue with the log, then find out what is filling up the logs. Look to the cause not the result.

---

### Post by hangle on 2012-08-17
My question about removing the files from a live disk is why
would I be more successful in this mode?

---

### Post by hangle on 2012-08-17
At least my problem is forcing me to learn a few things about the OS.  The files I am trying to delete are in a deep directory under '/sys/devices/'.   The file feature 'ioctl'  raises an ENOTTY error when it is configured on a file that is not a terminal.   I suspect that the files in question are regular files that the system has tagged as devices. I doubt that the system would allow me to removes these "devices"?

---

### Post by lukeiamyourfather on 2012-08-17
> **hangle said:**
> ...I doubt that the system would allow me to removes these "devices"?

That's why you do it from a live disc instead of on the hard disk the system is currently running from.

---

