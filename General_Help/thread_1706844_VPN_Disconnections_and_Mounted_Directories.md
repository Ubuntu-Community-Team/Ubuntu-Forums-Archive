---
title: "VPN Disconnections and Mounted Directories"
date: 2011-03-14
forum: General Help
---

### Post by kingdogbert on 2011-03-14
I use a VPN connection to access my university's computer system and remote directory mounting to access my files there. 

```
sshfs <remote dir>: /media/remotedir
```

Unfortunately, the VPN connection is unreliable and often fails. If it fails while I have the remote directory mounted, it causes all kinds of problems.

1) It locks up the mount location, so I can't unmount
2) It locks up the GUI file browser (e.g. I can't open any folders in 'Places')
3) It locks up any applications that were accessing remote files (e.g. If I was viewing a PDF in Okular, I can no longer launch Okular from either 'Application' or from a terminal; failing to launch from terminal freezes the terminal instance as well, which ignores even ^C and ^Z)

Restarting GNOME doesn't fix the problems. The only solution I've found is a system reset, which is not ideal. Is there a better way to get the frozen programs restarted? Thanks

---

### Post by kanikilu on 2011-03-14
Someone asked a similar question on another site - the OP doesn't say if it helped, but someone posted a couple suggestions to try:

[http://serverfault.com/questions/217240/failing-sshfs-connection-drags-down-the-system](http://serverfault.com/questions/217240/failing-sshfs-connection-drags-down-the-system)

There's a related, long-standing, bug open in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/159031](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/159031)

Unfortunately, it doesn't look like it's going to be resolved anytime soon :-/

---

