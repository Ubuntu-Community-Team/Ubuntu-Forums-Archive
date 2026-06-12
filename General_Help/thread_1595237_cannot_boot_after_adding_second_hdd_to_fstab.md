---
title: "cannot boot after adding second hdd to fstab"
date: 2010-10-13
forum: General Help
---

### Post by miles916 on 2010-10-13
hi everyone!

my installation is acting really strange since i upgraded to maverick. i managed to get a fresh install running, but when i added a line to fstab to automount my second hdd, i seem to have hit a dead-end. 

at first, the second hdd just didnt mount, because i had made a mistake in the uuid. after correcting this, it still wouldnt mount (something seemed to be wrong with the mount point), so i commented out the line in fstab. 

since doing this, i cant seem to boot up at all any more. 

what happens is, everything boots normally up to a desktop session. i see a popup that my login keyring is still locked, and that i should unlock it (i think this is ubuntone asking for authentication to sync). the problem is, i can move the mouse pointer, but theres no cursor. i cant enter my password, i cant close the window or do anything else for that matter. 

i know that my hdds are configured to remount as read-only wenn errors occur, and im assuming that something like this is happening now. 

i forced fsck on boot, and it seemed to have checked my system disk, but i still cant boot... i get to the unlock login keyring prompt, then nothing. the hdd seems to be active (its constantly reading), but nothing is happening.

does anyone have any suggestions how to check for hdd errors on my system partition and the swap partition, that outputs any useful data? 

regards, M.

edit: removed gnome-do and a couple of unused packages in tty1 (incl. a "lib-gnome-keyring" package). bootup worked now.

---

