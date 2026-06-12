---
title: "Log messages"
date: 2011-09-01
forum: General Help
---

### Post by pravindra.kumar on 2011-09-01
Dear All,
I am having some messages related to cups when i run "tail -f /var/log/messages". Can anyone make me understand that why these messages are coming, if any problem with system then how can fix it.
Messages are following :-

root@xubuntu-desktop:~# tail -f /var/log/messages
Sep  1 14:56:39 xubuntu-desktop -- MARK --
Sep  1 15:16:39 xubuntu-desktop -- MARK --
Sep  1 15:36:39 xubuntu-desktop -- MARK --

Sep  1 15:50:19 xubuntu-desktop kernel: [157735.048788] audit(1314872419.693:57): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=27881 profile="/usr/sbin/cupsd" namespace="default"

Sep  1 16:10:51 xubuntu-desktop kernel: [158964.617328] audit(1314873651.688:58): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=28560 profile="/usr/sbin/cupsd" namespace="default"

Sep  1 16:36:39 xubuntu-desktop -- MARK --

Sep  1 16:42:43 xubuntu-desktop kernel: [160872.956001] audit(1314875563.792:59): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=29537 profile="/usr/sbin/cupsd" namespace="default"

Sep  1 16:47:50 xubuntu-desktop kernel: [161179.538968] audit(1314875870.980:60): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=29725 profile="/usr/sbin/cupsd" namespace="default"

Sep  1 17:16:39 xubuntu-desktop -- MARK --

---

