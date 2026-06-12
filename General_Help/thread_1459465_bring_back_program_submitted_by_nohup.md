---
title: "bring back program submitted by nohup"
date: 2010-04-21
forum: General Help
---

### Post by searland on 2010-04-21
I had a make file which deals with hundreds of thousand jpeg images.
I submitted this job by using:
  nohup make &
Is there any possible way that brings this program back to foreground? I can only use ps to monitor the status, command jobs cannot find it.

Thanks.

---

### Post by gmargo on 2010-04-21
Assuming you're using Bash, a simple "fg" will bring it back to the foreground.  But that won't change the output redirection, which will still be going to ~/nohup.out.

If the command "jobs" cannot find see it, then it is no longer a child of this shell.  If you do a ps you'll see it is now owned by process 1 (init).  That cannot be "brought back to the foreground" because the foreground no longer exists.

---

