---
title: "Shutdown command hanging"
date: 2010-09-02
forum: General Help
---

### Post by Michael__ on 2010-09-02
Hi all,

On Ubuntu 10.04, I am able to shutdown with no problems using the panel button.  But when I do a deferred shutdown with 'sudo shutdown +5', the shutdown hangs.  The Ubuntu splash screen comes up, and each dot ticks away from red to white in the animaion, but that last dot never changes, and the system never shuts down.

An immediate shutdown with 'sudo shutdown +0' hangs similarly.  Any ideas?

Michael

---

### Post by llamabr on 2010-09-02
I've never used the + sign.  how about this:

```
sudo shutdown -h now
```

---

### Post by Michael__ on 2010-09-02
Okay, let me try th

---

### Post by Michael__ on 2010-09-02
How I jest.  But seriously, it worked fine.  Thanks.

Apparently, the -h switch was needed, because it now works fine either with 'now' or a deferred shutdown (I tested +1 minute).

So:  Halting is key.

Thanks again.

---

### Post by James78 on 2010-09-02
I find using "halt" and "reboot" to be faster, but they really do the same things.

Shutdown:
sudo shutdown -h now
sudo halt

Restart:
sudo shutdown -r now
sudo reboot

---

### Post by llamabr on 2010-09-02
Ya, that don't like for us to tell you to read the man page, but shutdown's man page is good.

-h is for halt
-r is for reboot

and you can mess with the time, and the other stuff too.

Well done.  be sure to change the subject to 'solved'.

---

