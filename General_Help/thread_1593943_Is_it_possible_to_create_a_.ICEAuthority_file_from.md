---
title: "Is it possible to create a .ICEAuthority file from the shell?"
date: 2010-10-11
forum: General Help
---

### Post by AshToTheLeigh on 2010-10-11
I might be asking the wrong question, I'm not sure. But here's what's happened so far:

Upon trying to login, I got 3 error messages in a row:
1. could not update ICEauthority file /home/ashleigh/.ICEauthority
2. there is a problem with the configuration server (/usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256
3.Nautilus could not create the following required folders: /home/ashleigh/desktop, /home/ashleigh/.nautilus Before running nautilus, please create these folders or set permissions such that nautilus can create them.

In this thread ([http://ubuntuforums.org/showthread.php?t=1563658](http://ubuntuforums.org/showthread.php?t=1563658)), it was recommended that another user with the same errors follow these instructions ([http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-9-10-cannot-log-in-777406/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-9-10-cannot-log-in-777406/))

I tried to follow those instructions as well, but got stuck in the very first step. Typing "ls -l /home/ashleigh/.ICEAuthority" produces an error that says there is no such file or directory.

Can I create that file from that text console? If so, how do I do it? (I'm new to linux in general, so I may need fairly step-by-step instructions) ...and if I can't create that file, then how should I proceed? I've only been using linux for a little bit now, but it's already driving me nuts that I can't login to the desktop environment.

---

### Post by AshToTheLeigh on 2010-10-12
If anyone has any idea what I need to do, please let me know! Thanks in advance :)

---

### Post by WorMzy on 2010-10-12
Sounds like you've really messed up your permissions and/or rm'd something you shouldn't have. What is the output of ```
ls -l /home
``` and ```
echo ~
```

---

### Post by AshToTheLeigh on 2010-10-12
Thanks for the response, WorMzy!

ls -l /home gives me:
```
total 12
drwx------ 39 ashleigh ashleigh 12288 2010-10-11 03:09 ashleigh
```

and echo ~ gives me:
```
/home/ashleigh
```

---

### Post by WorMzy on 2010-10-12
Well that all looks fine.

I know you said you tried to ls -l /home/ashleigh/.ICEAuthority, but did you put a lowercase "a" or capital "A" for "authority"? It should be lowercase, so try that.
```
ls -l /home/ashleigh/.ICEauthority
```
Also check
```
ls -ld /home/ashleigh/Desktop
```
and
```
ls -ld /home/ashleigh/.nautilus
```

---

### Post by AshToTheLeigh on 2010-10-12
You're a genius!! It was indeed the A/a that was the problem. I was able to follow the steps of the other thread, and am typing to you from Linux as we speak :D

Thank you thank you THANK YOU!! **happy**

---

### Post by WorMzy on 2010-10-12
No worries. It's not the first time case-sensitivity has led to confusion, and I doubt it'll be the last either. :)

Enjoy~

---

