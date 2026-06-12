---
title: "Unable to list folder contents"
date: 2011-04-08
forum: General Help
---

### Post by MTO on 2011-04-08
Hello,
I am unable to open my home user folder.
Both in nautilus and terminal I have the same problem.

It just stays there working forever, hours... and nothing.
I am unable to enter my home folder.

I tried restarting the computer, in hope it would get autofixed, but nothing. I am completely unable to enter my /home/user/ folder, please help!


Ubuntu 10.10

**I did search for this.*

---

### Post by adit on 2011-04-08
What happens after typing:
ls
and pressing enter. Does the command prompt return or not?

---

### Post by MTO on 2011-04-08
Nothing, it just starts a new line as waiting, waiting, and waiting...

---

### Post by tredegar on 2011-04-08
This is not normal behaviour.

What did you do to cause this to start (not) happening ?

We need some clues if we are to help solve your problem.

---

### Post by MTO on 2011-04-08
Nothing that I know.
It might have been coincidence, but when I tried to mount an external drive I noticed I wasn't able to access my home folder from where I need to copy some files. Yesterday I did access it without any problem. Nothing new, nothing newly installed, etc. No idea.

---

### Post by MTO on 2011-04-08
I am able to get into known folders under my user folder such as:
/home/user/Documents/
/home/user/Things/

But when I try to see things under:
/home/user/
nothing happens, neither in nautilus nor terminal.
*ls does not give any reply.*

---

### Post by AlphaLexman on 2011-04-08
Where did you try to mount the external drive, to /home/user/ or to /media/ ??

Is the external drive mounted correctly? Have you tried access /home/user with the external drive NOT mounted or even plugged in?

If any of these seem to be an issue, post the contents of /etc/fstab

---

### Post by MTO on 2011-04-08
Drive (sd card) was mounted to /media/ 

After reading your suspicion that it might have something to do, I tried to unmount it... was unable though nautilus. So I used the disk utility and was able to do so from there. Still unable to enter my user home folder. I restarted, and now **everything is back to normal.**

Thanks for your help!
Your tip on it having something to do with the mounted drive helped!

Weird it would affect home/user in some way, but anyway, it's fixed!

---

### Post by khuffmanjr on 2011-04-14
I experienced this same issue today and finally happened across this thread.  Thanks for posting.

My issue was related to an NFS export mounted at ~/mnt that I forgot to umount before suspending earlier.  I was unable to 'ls' in home or open nautilus in home.  After forcibly umounting the no-longer-connected export, all returned to normal.

Ubuntu 10.10 as well.   By the way, I found references to this issue and .gvfs on the fedora boards.  Seems to be related.  Good day!

---

