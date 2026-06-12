---
title: "Automated backup to server"
date: 2010-01-29
forum: General Help
---

### Post by Jackelope on 2010-01-29
I come before you, Ubuntu gurus, to seek your collective wisdom.

I have a laptop running Ubuntu 9.10. My important data is on an NTFS partition on said laptop (it has to be NTFS for sharing with Vista on another partition). I also have a server running XP. I need to run an automated backup from my laptop to the server daily. But so far nothing has worked, including Sbackup, BackinTime, Union, and Allwaysync. Here's what I need that data to do:

Files in pass protected NTFS partition -> Ubuntu OS -> (over network) -> XP Server.

Sounds simple enough, but nothing has worked. Is there a better way? FTP? Linux on the server maybe? If you have an idea, please let me know. Thanks ahead of time! :D

---

### Post by quixote on 2010-01-30
It's been a while since I was in a similar situation, so this info may be dated or no longer right.  I my case, the server ran a version of linux, so that's another big difference.  (It's a lot easier to get linux to talk to other OSes, than the other way around.  There's a reason why some huge majority of servers run unix/linux :).)  What I had to do was:

edit /etc/nsswitch.conf:
change 			hosts: files dns mdns
  to this:		hosts: **wins** files dns mdns
and check synaptic to make sure winbind and nfs-common are installed.

Then restart both the server and your laptop, and the two should (might?) magically see each other.

Note: in karmic a few weeks ago there was a bug so that installing winbind made synaptic stop working.  They may have fixed it by now.  Since you're on Jaunty, it's not an issue, but just so you know.

None of this says how to negotiate the necessary authentication since the ntfs partition is password protected.  Mine wasn't, so I have no suggestions there.

Is there a reason why the ntfs backup has to go via ubuntu?  Surely, the ntfs and the XP machines can see each other?  I don't know, but wouldn't a direct backup between the two be easier to set up?

As far as the backup scripts themselves go, I had much the same experience as you.  I wound up jimmying [Mike Rubel's script]("http://www.mikerubel.org/computers/rsync_snapshots/") for my own set up. The [linux time machine]("http://blog.interlinked.org/tutorials/rsync_time_machine.html") thing also looks interesting, but I haven't tried it.

---

