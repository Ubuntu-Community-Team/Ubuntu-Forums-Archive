---
title: "Google Chrome doesn't open, incorrect permissions. 11.04"
date: 2011-09-17
forum: General Help
---

### Post by yonni on 2011-09-17
Hi guys,

I just installed Ubuntu 11.04 on my new laptop and I'm pretty happy with it. But after a restart Chrome (that's Google Chrome, not chromium) will no longer open. When running from the terminal I get the error:
```
[1601:1611:838108318:ERROR:shared_memory_posix.cc(158)] Creating shared memory in /dev/shm/.org.chromium.Chromium.hb5Es7 failed: Permission denied
[1601:1611:838108431:ERROR:shared_memory_posix.cc(161)] Unable to access(W_OK|X_OK) /dev/shm: Permission denied
[1601:1611:838108478:FATAL:shared_memory_posix.cc(163)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
Aborted
```
(N.B. my error may differ slightly, I copied this one from another thread since I can't reproduce the problem without restarting, which I don't have time for. Copied from this thread: [http://ubuntuforums.org/showthread.php?t=1803889](http://ubuntuforums.org/showthread.php?t=1803889))


If you do 'sudo chmod 1777 /dev/shm' you can then open chrome, and it works fine until a restart. What keeps changing the permissions back and how can I fix it?

N.B. the thread I linked to above is about Chromium in 11.10 beta, not google-chrome in 11.04 as I'm using. Something somebody suggested on the second page is to do:
```
none /dev/shm tmpfs defaults 0 0
```
in fstab. What will this do? I'm pretty confused as to why this is a problem.

Thanks for your help!

---

### Post by mebunto on 2011-09-17
I've been running Chrome on Natty for months without a problem.  It was "upgraded" yesterday and now doesn't start.  I've tried uninstalling and installing, purging and installing using dpkg .... nothing works.

---

### Post by mebunto on 2011-09-18
I've managed to solve my problem.  The issue was with permissions of .cache, which were 755.  I changed them to 757 and now chrome starts.

---

### Post by psrdotcom on 2011-09-18
useful !!

Please mark thread as solved.

---

### Post by vasa1 on 2011-09-18
> **psrdotcom said:**
> useful !!

Please mark thread as solved.

Interesting that setting 757 does the trick. I'm just finding my way around Linux, but isn't 757 less "secure" than 755? And then why not just 777?

BTW, I'm still waiting for the Chrome 14 update to be pushed my way.

---

### Post by yonni on 2011-09-19
Thanks for this!

---

### Post by mebunto on 2011-09-19
Glad it was of help. I'm no guru - permissions are Owner Group Other.  Presumably Chrome must be the "other" when it runs and needs write permission for .cache therefore the write bit needs to be set.  If it were 777 then the owner's Group would have write permission too, does I make a difference?  I don't know.  From a security purist's point of view then everything should be prevented from doing anything .... then you allow access that is required, rather than everything being able to do anything and having no idea of what is doing what.  Am I making sense?

---

