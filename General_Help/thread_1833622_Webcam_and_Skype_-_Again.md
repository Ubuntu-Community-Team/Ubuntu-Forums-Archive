---
title: "Webcam and Skype - Again"
date: 2011-08-26
forum: General Help
---

### Post by felipeabrao on 2011-08-26
Hello everybody,

I know that there are many posts about incompatibility between webcams and Skype for Linux. I read many of them and looked for other solutions in the web, but I really could not solve my so common problem: the webcam works with other programs, but not with Skype. I tried the command 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

but it did not work. Skype was openned, but the problem persisted, and in the terminal the following message was written:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

If somebody could help me, I would appreciate it. 

Thanks in advance,

Felipe

PS: I use Ubuntu 11.04.

---

### Post by felipeabrao on 2011-08-27
OK, the directory libv4l was in another directory! I do not know why it was in /usr/lib/i386-linux-gnu/libv4l. I used then the command LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype &, and it worked!

Thank you,

Felipe

---

