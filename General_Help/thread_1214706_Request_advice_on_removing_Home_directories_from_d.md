---
title: "Request advice on removing Home directories from desktop"
date: 2009-07-16
forum: General Help
---

### Post by HKAlly on 2009-07-16
Hi Somehow I have managed to end up with the contents of my home directory (all the directories in it) displayed on my desktop and the link to my home directory in the Places panel of my File Browser has gone. This only appeared when I booted up this am. Can someone please advise what I have done and how I can revert to a clear desktop with a link to my home directory in the Places panel If it is relevant I'm using Jaunty on a Dell latitude E6400  Cheers

---

### Post by nikhilk on 2009-07-16
What are the contents of your home directory? I mean, have the contents from your home been copied to desktop or moved?

---

### Post by az on 2009-07-16
Maybe you changed the location of your desktop to point to your home directory.  See here:
[http://ubuntuforums.org/showthread.php?t=373057](http://ubuntuforums.org/showthread.php?t=373057)

---

### Post by HKAlly on 2009-07-16
> **nikhilk said:**
> What are the contents of your home directory? I mean, have the contents from your home been copied to desktop or moved?

Hi I can see all the folders in my home directory on my desktop. When I click on desktop in Places I can see all my home folder in the browser window. and the location is given as /home/*myname* my home folder. But previously I had *myname* in the Places Panel and a clear desktop.  If I click File System in the Places panel I can see /home and if I click on that I also get to /home/*myname* with all my folders in it. 

Hope this helps to clarify.

---

### Post by HKAlly on 2009-07-16
> **az said:**
> Maybe you changed the location of your desktop to point to your home directory.  See here:
[http://ubuntuforums.org/showthread.php?t=373057](http://ubuntuforums.org/showthread.php?t=373057)

hi that is the opposite of what I wnat to do but I tried ticking the box refered to rebooting the system unticking the box and rebooting the system again and it did not change the home folder contents are still displayed on the desktop but thanks for replying

---

### Post by michy99 on 2009-07-16
What output do you get from these two commands?```
ls -la ~
ls -la ~/Desktop
```

---

### Post by az on 2009-07-16
> **HKAlly said:**
> hi that is the opposite of what I wnat to do but I tried ticking the box refered to rebooting the system unticking the box and rebooting the system again and it did not change the home folder contents are still displayed on the desktop but thanks for replying

Was it set to /home/user/Desktop?  If it's not, then that's your problem...

---

### Post by HKAlly on 2009-07-17
> **michy99 said:**
> What output do you get from these two commands?```
ls -la ~
ls -la ~/Desktop
```

Hi for 

*myname*@*mycomputername*:~$ ls -la ~/Desktop
ls: cannot access /home/*myname*/Desktop: No such file or directory

but sudo  ls -la ~/Desktop gets a list similar to that with  ls -la ~

and *myname*@*mycomputername*:~$ ls -la ~ give a list that includes all my home directory folders that are on the desktop plus drwxr-xr-x  4 root     root ; and *various permissions* *myname* *myname* *size date time* .bash_history; .config; .gnome; .nautilus; .VirtualBox for example and many more.

Does that help?

---

