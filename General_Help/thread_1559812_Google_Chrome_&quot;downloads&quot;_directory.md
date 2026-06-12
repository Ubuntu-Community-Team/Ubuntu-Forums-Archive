---
title: "Google Chrome &quot;downloads&quot; directory"
date: 2010-08-24
forum: General Help
---

### Post by thezwallrus on 2010-08-24
Hi all,

I'm getting my head around my first Linux OS, and I'm dual-booting Ubuntu 10.04 with Windows 7. I've done a pretty good job of synchronizing everything between the two OS's. I have my ubuntu and windows user directories pointing to a separate NTFS partition, with Google Chrome's app data in a folder under App Data on the third partition. However, I can't get Google Chrome to download to the same directory on Ubuntu and Windows, and here's why:

The downloads directory is part of the app data, not part of the shortcut. So if I tell it to point to G:/downloads or {/home/user/downloads | /media/user-data/downloads}, it won't work on one of them. Could I use some type of alias or symlinking scheme to have one choice point to two different locations depending on the OS?

---

### Post by thezwallrus on 2010-08-24
I got it working kind of hackishly. It turns out that when I put /home/user/Downloads in it, in windows it defaults to C:\home\user\Downloads, so I created a symlink from this folder to G:\Downloads.

If there are any other ideas, cool.
Gonna mess with Firefox too.
Then maybe LAMP / WAMP

---

