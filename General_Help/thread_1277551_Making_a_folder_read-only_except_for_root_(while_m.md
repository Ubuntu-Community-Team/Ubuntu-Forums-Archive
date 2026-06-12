---
title: "Making a folder read-only except for root (while maintaining file permissions)"
date: 2009-09-28
forum: General Help
---

### Post by undecim on 2009-09-28
I have a snapshot script I've written that uses rsync (an amazing piece of software!) to create daily snapshots of /var/user-backups/current/ to /var/user-backups/snapshots/`date +%F`/ (with the -a option, and --link-dest on previous snapshot, etc, to save space).

The problem is, the people who are going to be using this server to backup their files aren't going to listen to me if I tell them that they shouldn't make changes to anything in the snapshots/ directory (which could really foul up the snapshots)

Is there some way that I can make the snapshots directory read-only for all users with the exception of root, while still preserving file permissions?

I've tried making a directory in /root/ and mounting it somewhere else with -o bind,ro, but it's still writable by everyone on the new mountpoint.

---

