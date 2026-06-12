---
title: "How to remove corrupted files on live distribution"
date: 2011-09-04
forum: General Help
---

### Post by lfiala on 2011-09-04
I have the live distribution on 32GB flash disk. It's Ubuntu 10.10. I suppose, that my problem was caused as I tried to upgrade on Ubuntu 11.04. I cancelled the upgrade process in beginning (but it looks like a bit late). When I later wanted install some application I noticed, that my software center doesn't work. There was corrupted /var/lib/dpkg/status file. In this forum, I found solution. So I fixed it by copying the status-old file. But I hit another problem. The file available is corrupted.
[B][COLOR=DarkGreen]root@ubuntu:/var/lib/dpkg# ll
-?????????  ? ?    ?          ?                ? available
-rw-r--r--  1 root root       0 2011-09-04 11:35 available-new
-?????????  ? ?    ?          ?                ? available-old[/COLOR]
[/B]I can't remove it, overwrite it nothing. I can't use the fsck util, because it writes me, that the device is in use. Can anyone help me?

---

### Post by dino99 on 2011-09-04
sudo rm /path/to/that/borked/file

---

### Post by lfiala on 2011-09-04
> **dino99 said:**
> sudo rm /path/to/that/borked/file

Thank you for you fast reply. But i think, that solution will not be so trivial. It's problem of file system.
[B][COLOR=DarkGreen]ubuntu@ubuntu:dpkg >sudo rm available
rm: cannot remove `available': Input/output error
[/COLOR][/B]

---

