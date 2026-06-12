---
title: "intall updates --&gt; boot failure"
date: 2009-12-08
forum: General Help
---

### Post by Ampi on 2009-12-08
Yesterday there were new updates to install, so I installed them. They required a reboot of the system. When this happened, suddenly my /data partition couldn't be read. Instead of the 300+GB with a lot of files and directories it now was 2B with nothing. This has happened [before]("http://ubuntuforums.org/showthread.php?t=1320320") to me.
This was then solved by a couple of reboots and now the same 'solution' helped. 
But the next time after the solving that I reboot, I get the error

Mount of root filesystem failed.

I've tried all te solutions I could find on the internet yesterday, but nothing worked. I've been up all night.
Other errors I got doing this are:

one or more of the mounts listed in /etc/fstab cannot et be mounted waiting for UUID.

On the same thread as mentioned above you can see my /etc/fstab and /etc/mtab.

What can I do? Are both problems (the loss of hte /data partition and the boot failure) related to each other?

---

### Post by Ampi on 2009-12-08
Okay, problem solved.

Together with another user on the forum we're trying to work out problems around samsung phones and ubuntu.
This also included an edit in my /lib/udev/rules.d/60-persistent-storage.rules.
I rebooted my computer before I saw an edit in the post that I shouldn't reboot with the edit made, hence the boot failure. I undid the edit and now my computer boots just fine.

---

