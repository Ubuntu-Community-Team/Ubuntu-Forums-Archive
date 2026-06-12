---
title: "crashplan +"
date: 2011-03-23
forum: General Help
---

### Post by frrobert on 2011-03-23
I am running crashplan+ on Ubuntu 10.04 and I noticed an issue.

I am backing up my computer to 2 locations.
The first being their online servers. That works fine.

The second location is a folder.

This is where the issue is.

If the mount point is /media/sg160 and crashplan stores the files in /media/sg160/crashplan everything works fine if the drive is connected.

The problem is if the drive is a removable drive or a network drive that for some reason currently is not accessible rather then generating an error and not running the backup it creates the directory crashplan under the directory /media/sg160/ and starts a fresh backup storing the backup under the new directory.

By the look at the crashplan forum this has been an ongoing issue for over a year and so far no fix.

The only work around I could find was a creating a shell script that turns off crashplan if the drive is unaccessible. The only problem is that also turns off the other backup to crashplan server.

Has any one come up with a work around for the problem?

I have also tried the following

I set the permissions on the mount point /media/sg160/ to 444.  Thinking that when sg160 is available it will mount over the directory and if sg160 is not available then crashplan will not be able to write to the directory.

The problem is even though the permission is 444 root who runs crashplan can still write to the directory sg160 when the drive is not mounted.

Any ideas?

---

