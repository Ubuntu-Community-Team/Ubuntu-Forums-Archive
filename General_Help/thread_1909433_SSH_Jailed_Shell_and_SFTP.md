---
title: "SSH Jailed Shell and SFTP"
date: 2012-01-15
forum: General Help
---

### Post by jfreak53 on 2012-01-15
I need to setup a dual setup for a jailed shell. My users need to be able to login to SSH shell in their user directory and also be able to SFTP in and SCP so they can sync files using rsync.

For the shell I got it fixed, on another server I used lshell, it works great since it allows me to cancel certain things and log them out automatically if they try something they shouldn't.

So the first part works, though lshell supports SCP and SFTP it doesn't jail them in their home directory. It jails shells but not SFTP or SCP.

So I need a way to do both.

I have OpenSSH 5.8p1

I have tried this:

Match user uname
  ChrootDirectory /home/%u/
  ForceCommand internal-sftp

But for some reason once I use that it won't let the user SFTP login anymore. I think it has to do with permissions from what I found on Google. But I'm not sure.

Any ideas? I have to be able to do both, jail SFTP and shell. Thanks.

---

### Post by jfreak53 on 2012-01-17
Just figured it out like 2 min. ago, no where on the NET and searching for this on Google did I find this. It seems that the folder you put down has to be owned by root:root.

No where did I ever read this on any tutorial on this I found, so oh well, for anyone searching in the future. So instead of /home/%u I just did /home and it works now.

Thanks.

---

### Post by polki@mac.com on 2012-01-18
I haven't tried it, in fact I only just read about it, but how about installing "scponly"?

---

### Post by Lars Noodén on 2012-01-18
> **jfreak53 said:**
>  It seems that the folder you put down has to be owned by root:root.

It's actually in the manual page for [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html), but it is easy to miss:

[indent]"*All components of the pathname must be root-owned directories that are not writable by any other user or group.* "[/indent]

---

