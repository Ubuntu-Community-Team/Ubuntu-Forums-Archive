---
title: "Problem: backintime fails, b/c new permission problem."
date: 2011-10-16
forum: General Help
---

### Post by fisheater on 2011-10-16
Hi all:

Problem: backintime fails, b/c new permission problem.

Background: Back In Time 1.0.6, ubuntu 11.04 64 bit. Was working flawlessly until 10 days ago. Then I noticed that it was getting hung on a particular file. 

Log: [E] Error: rsync: send_files failed to open "/home/stonemason/Documents/crusty/crusty_old_file.odt": Permission denied (13)

I checked the permissions on the file, matched all the other ok files/folders.

So then the misadventure began, I searched for a solution. I tried chown, typed wrong user, then chmod, then lots of sweating until I was able to restore the correct owner:group. Now I am back where I started. 

I haven’t been doing anything with permissions on my computer (before my misadventure).

Backintime runs flawlessly as root.

Suggestions on how to resolve this error 13?

Kind regards,

FE

---

### Post by fisheater on 2011-11-14
This post was likely lost in the quick moving posts of the new release. This is a goodbye to my old friend backintime.

This is an update to say this remains unsolved, despite multiple attempts to fix permissions.

Interestingly I am able to use rsync to backup my /home without issue. Now that I have a bit more experience with rsync, terminal, and cron I have switched to that method of backup.

FE

---

