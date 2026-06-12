---
title: "Rotating Server Backups with Hard Drives"
date: 2011-10-24
forum: General Help
---

### Post by Joshua on 2011-10-24
I'm trying to set up a relatively automated system for making server backups using USB Hard Drives.

The plan would be to have someone plug-in a portable USB disk at the start of a weekly rotation.  rsync would update the backup every night and at the end of the week the disk would be taken to an off-site facility and a new one would be added.  There would be several disks in the rotation, so the oldest one in the off-site facility would be used as the replacement.

The problem is that the administrator won't be on-site all the time, and even if he were, I don't want the process to require a log-in.  I want anyone near the server to just unplug the old drive and plug a new drive in and for everything to work - similar to the amount of interaction a tape-based system would need.

How do I ensure the new disk gets assigned the correct device name?  Or if I use a script to do the mount, how to I ensure that the correct device is mounted?

---

### Post by cryptotheslow on 2011-10-24
I'd have thought if you give the exact same label to the partition on each of the USB drives they would always get mounted into the same place in /media

e.g. label the partition on each of the drives BACKUP and they should get mounted to /media/BACKUP

Seems too simple though, so I'm likely wrong! :D

---

### Post by decoherence on 2011-10-24
Hi,

Not having done this, I can only suggest where you might get started. First, do what cryptotheslow suggests and give them all the same label. It's a reasonable suggestion and could be all you need!

To get a better idea of what is going on, run 'udevadm monitor' on the server and plug each drive in, one at a time. This will tell you where it gets mounted so you can see if they end up in the same place. If they don't, udevadm will also tell you what rule it is using to assign the device name. You may need to modify or add a rule to handle these. What you are suggesting can definitely be done with udev rules, if it doesn't work already.

I would also suggest, as part of your backup script, sending an email to the admin so that s/he can confirm whether the backup ran. If you have your own smtp server, you can either write an expect script to telnet in to it or install one of the minimal smtp mail agents (can't recall what they're called off the top of my head) to sent an email from your script.

Good luck! I'd like to hear about your progress as I would like to eventually implement something similar.

---

### Post by Joshua on 2011-10-24
Wow.  That does seem really simple, and I'll have to try that.  Also, I didn't know about the udevadm tool, so that will be helpful when setting everything up.

The first place I was going to do this, though, is on a CentOS box.  I had planned to use scripting, cron, and rsync - which should be almost the same on any version of Linux, but if CentOS has a similar mounting process, that would probably be a much easier solution.

---

### Post by Joshua on 2011-10-24
Oops.  I was researching this and I just realized that this might not be compatible with how I intended to mount/unmount the USB disks.

I've read that when using hard disk drives for backup media, one should only mount the device when it is needed, and then unmount the device when the backup is complete.  I think the expectation is that this will help prevent file corruption in case of power surges.

Is that approach necessary?  And even if it's not necessary to do that, my script will need to check for a mounted backup drive and fail gracefully or attempt to mount the drive if not detected - just in case the drive is unmounted.

---

