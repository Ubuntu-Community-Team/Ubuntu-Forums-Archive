---
title: "I never like seeing &quot;Permission Denied&quot;."
date: 2010-04-02
forum: General Help
---

### Post by EMABrad on 2010-04-02
So I'm running Karmic on my HP laptop (can't remember the exact model), and I'm dual-booting with Vista.  I have a separate partition for each of those, plus a swap partition and a partition for music, pictures, videos, and other documents.  I didn't have the documents partition set to be automounted, so when I booted the computer and then ran Amarok (my current music player for Ubuntu) without mounting, it ran around and panicked until I manually mounted it, which was bothersome.  I downloaded an drive manager that could automount, if I recall (I can't BELIEVE I can't remember what it was called), and in a stroke of complete idiocy, just went in and clicked some buttons and quit.  When I try to reboot into Ubuntu (be it recovery mode or not), I get several lines of messages akin to:
```
init: job_process.c:529: unhandled error from job_process_spawn: permission denied
```
I can guess what this means.  What can I do to fix this?

---

### Post by EMABrad on 2010-04-02
Well, it's that line, that it shows, but it also shows a lot of:
```
init: Failed to spawn mountall-shell pain process: unable to execute: Permission denied
```
Life sucks.

---

### Post by EMABrad on 2010-04-02
All right, the program was pysdm.  I've seen a lot of people with problems here.  Help?

---

### Post by renkinjutsu on 2010-04-02
I haven't used ubuntu for a while, but my only guess is that some files in your /etc/init.d are not set to be executable.. try setting them with ```
sudo chmod -R +x /etc/init.d/
```

---

### Post by EMABrad on 2010-04-02
But I can't even get into Ubuntu.

---

