---
title: "Not booting"
date: 2006-02-03
forum: General Help
---

### Post by thessem on 2006-02-03
When I try to boot ubuntuu I get the following error message,

Begin: Running /scripts/local-premount
[4294675.50800] Attempting manual resume
[4294675.519000]swsusp: suspend partition has wrong signature?
Done.
[42944675.570000]EXT3-fs error (device md0):ext3_check descriptors: Block bitmap for group 0 not in group (block 1480871497)!
[4294675.530000]EXT3-fs:group descriptors corrupted!
mount: Mounting /dev/root on /root failed: invalid argument
Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
Done.
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory

Target filesystem doesn't have /sbin/init

BusyBox v1.00-preto (Debian 20040623-1ubuntu22) Built in shell (ash)
enter 'help' for a list of built in commands

/bin/sh: can't access tty; job control turned off
# " this is the prompt- this is where it stops"

I havnt changed anything recently, exept for a kernel upgradebut that was more than a week ago.

What is wrong with my system?

---

### Post by dcstar on 2006-02-03
[QUOTE=thessem]
......
I havnt changed anything recently, exept for a kernel upgradebut that was more than a week ago.

What is wrong with my system?[/QUOTE]
Looks like filesystem corruption or a faulty hard drive.

Start up in recovery mode and log in as root, and then run fsck.

---

