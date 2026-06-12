---
title: "high download speeds in rtorrent freezes server"
date: 2009-11-20
forum: General Help
---

### Post by ltlbkofjim on 2009-11-20
Hi Guys,
wonder if someone can help me.
I have Ubuntu 9.04 server with rtorrent installed which i access via ssh. This has been working perfectly until recently, and now everytime a torrent is added and fast download speeds are reached everything on the server freezes, no http, no ftp, no ssh and a manual restart is required to get it working again. This seems to happen every time a torrent is added that causes downloads to go above 2mb/s.

I have tried running it under various user accounts and have even reinstalled the OS in my frustration last night. However the problem still persists! if i throttle the bandwidth to 1mb/s, then it seems to run indefinately.

I have also tried renaming the rtorrent binary in case rtorrent was being blocked, however this did not help.

Does anyone have any idea's, happy to provide any other info or logs on request.

cheers

---

### Post by iggykoopa on 2009-12-16
I may have a similar thing happening, but it's been really hard to track down. When I'm running rtorrent I will have hard lock-ups like you intermittently, it also seems to happen sometimes if I use sshfs and try to transfer a lot of files. It seems to match a lot of the posts in this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all) bug report. I first had the issue a couple of months ago using 9.04 and wired network, I downgraded to 8.10 and ran stable for a couple months. I recently moved to 9.10 and am using wireless and the issue has returned. The only things that are the same on the system now compared to then are the motherboard, cpu, and ram.

---

### Post by TMavro on 2010-01-11
Have you tried adding/adjusting "max_open_sockets" in rtorrent.rc? Its default setting allowed more connections than my router could handle, and everything freezed. Allowing fewer sockets fixed this.

---

### Post by iggykoopa on 2010-01-13
Yup, and tried with only one download at a time, etc. Also this is on a different router than the one it happened on initially.

---

