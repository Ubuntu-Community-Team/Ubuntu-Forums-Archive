---
title: "How can I tell if POSIX shared mem. is enabled"
date: 2009-06-29
forum: General Help
---

### Post by Laysan_A on 2009-06-29
Hi, 

I compiled a 2.6.30 ultimate kernel using kernelcheck. I read that posix is enabled by default in ubuntu kernels, but since I compiled my own, and didn't look for it specifically when I configured, I don't know if my kernel is configured to use it.

Is there any way for me to tell, and if not, can I enable it  without recompiling the kernel from scratch?

(I'm wondering if this might be why I'm having problems with fglrx)

---

### Post by Brandon Williams on 2009-06-29
Run this command to see if POSIX shared memory is available on your system: 'mount | grep "shm"' If there is output, then you've got everything setup correctly.

---

### Post by Laysan_A on 2009-06-29
Thanks Brandon. 

I'm afraid the command sequence didn't work properly. Here is what I got:

> @DESKTOP:~$ mount grep | "shm"
mount: can't find grep in /etc/fstab or /etc/mtab
bash: shm: command not foundOkay, this time I copy/pasted (my eyes aren't what they were and I missed some punctuation the first time):

> @DESKTOP:~$ 'mount | grep "shm"'
bash: mount | grep "shm": command not foundSo, does this mean posix isn't enabled?

Okay, I did a little reading, and tried just issuing a mount command to see what comes out and I got this line:

> tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)

So, does this then mean that posix **is** enabled?

---

### Post by Brandon Williams on 2009-06-30
I meant for your to run the command line without the single-quotes. Probably should have mentioned that.

Yes, the fact that mount shows a tmpfs filesystem on /dev/shm indicates that posix shared memory is enabled. That's the line my command line was intended to help you find.

---

### Post by Laysan_A on 2009-06-30
Thanks Brandon. I guess I don't have any more excuses then. Time to start messing with my graphics again...

---

### Post by Bryan55 on 2010-01-28
Hi

I was wanting to find out the same. When I ran this command I got.

 mount | grep "shm"
none on /dev/shm type tmpfs (rw,nosuid,nodev)


So it looks like it is not.

Could someone tell me how to get it enable please?

I'm on Ubuntu 9.10

Thanks 
Bryan.

---

