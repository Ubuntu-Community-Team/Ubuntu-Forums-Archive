---
title: "network problem (between ubuntu, no windows system involved)"
date: 2009-11-18
forum: General Help
---

### Post by pearldrums on 2009-11-18
First off, I have looked at [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1169149&highlight=failed+retrieve+share+list+server") how to post.

I'm having issues networking between two computers, both running ubuntu. One is a laptop, one is a desktop. The desktop can always connect to the laptop's shared files, but the laptop has issues seeing the desktop's files. At first the laptop couldn't even see the desktop at all, but after checking the firewall settings and adjusting the samba config file I fixed that issue. Now when I try to access the desktop from the notebook it gives me the "could not mount.... cant find shares from network list" or something like that. However, if I restart samba I can then access the shared folders. How can I make this work on startup?

---

### Post by pearldrums on 2009-11-18
Alright, now I feel like a forum spammer and also incompetent. Things are magically working again after I have restarted samba. The thing is, I've restarted samba about 6 times today and there is no reason for a perminant change. I've tested the network 3 times now, re-booting both machines between each test and there no longer seems to be an issue. I don't know why it works now but it does. I'm still not going to mark this thread as solved for a couple of days just in case it stops working as magically as it started.

sorry for wasting your time.

---

