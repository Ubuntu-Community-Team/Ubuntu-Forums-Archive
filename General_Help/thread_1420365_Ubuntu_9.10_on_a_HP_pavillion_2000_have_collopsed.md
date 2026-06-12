---
title: "Ubuntu 9.10 on a HP pavillion 2000 have collopsed?"
date: 2010-03-03
forum: General Help
---

### Post by pgonzamailcn on 2010-03-03
Hi all,

After having my Ubuntu 9.10 for more than 2 months and being so happy about it, it has suddenly collapsed. I do not know if collapse is the best word to describe it but it looks like but hopefully has not.

It happened like this: I switched off the computer before leaving for a 10 days trip and no problems. When I came back and switched on the computer but it was impossible to start. The screen first showed the following message:

Mount of file system failed.
A maintenance shell will now be started.
CONTROL D will terminate this shell and re-try.
root@pablo-laptop:~#

I force the laptop to switch off and switch it on again. It gave me options to initialize under different versions of Karmic Koala but none work. (It gave me the option of making a memory (or file system, I do not remember well) test which I did and says there was no problem). In all the cases it went back to the message above.

I tried Control + D but again nothing. It displayed a page of information of which I write a part of it:

…

/dev/sda1: Superblock last mount time (Thu Feb 18 07:57:09 2010; now = Tue Dec 31 17:28:42 2002) is in the future.

/dev/sda1: UNEXPECTED INCONSYSTENCY; RUN fsck MANUALLY.

…

Mount of file system failed.
A maintenance shell will now be started.
CONTROL D will terminate this shell and re-try.
root@pablo-laptop:~#

To see all the info after Control + D you can see the attachement (althoug not too clear)

If you can not see well the picture and the info on it I can try to make it better or transcript it.

Do you have any suggestions?

Thanks in advance.

All the best,

Pablo

---

### Post by 3rdalbum on 2010-03-03
> /dev/sda1: UNEXPECTED INCONSYSTENCY; RUN fsck MANUALLY.

At the terminal prompt, type:

```
fsck /dev/sda1
```

Hit 'y' to everything it asks about.

---

### Post by pgonzamailcn on 2010-03-03
Hi,

Thanks a lot! It worked! I thought I lost all the information in the computer.

Why this happened? I would be happy if somebody could explain me the reason so I can prevent it.

After done as you (3rdalbum) told me the system get back to normal but I find something wrong with Firefox. A popout "Your browser has been updated and needs to be restarted". When I press to "Restart", it restart Firefox but again appear the same popout. Even after rebooting the laptop. Apart from that, when I visit any website it always direct me to the "Untrusted connection" and ask me for a certificate. What is the problem? Is it related with what I reported in the fist thread (/dev/sda1: UNEXPECTED INCONSYSTENCY; RUN fsck MANUALLY)? What other programs may be affected by this "problem"?

Thanks in advance!

Pablo

---

### Post by pgonzamailcn on 2010-03-03
Hi,

Me again.

Something very strange: the laptop date is now Thu Jan 2nd of 2003. How is this possible? At that time I even have this laptop. Thanks.

Pablo

---

### Post by pgonzamailcn on 2010-03-03
Sorry, I wanted to say "I even did not have this laptop"

---

