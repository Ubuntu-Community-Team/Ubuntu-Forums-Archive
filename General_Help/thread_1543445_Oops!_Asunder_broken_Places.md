---
title: "Oops! Asunder broken Places"
date: 2010-08-01
forum: General Help
---

### Post by bouncingwilf on 2010-08-01
I've posted this here rather than multi-media as it's not asunder I'm  trying to fix. I installed asunder last night to try and rip a CD but  could not get it to find the CD which was in a USB attached drive rather  that the main PC DVD drive ( Main Drive broke). I eventually gave up  and uninstalled asunder BUT now when I click on places on the top  application bar, I get an error message thus;

"Could not open location 'file:///home/wilf'
failed to execute child process "asunder"
(no such file or directory)


This error occurs for all locations attached to my home folder. Any tips  on how to restore the correct action would be much appreciated.


Bouncingwilf

---

### Post by Smart Viking on 2010-08-01
Hey, this looks like some weird bug, you could always try to reinstall the program by entering this command(to please the shortcuts):

```
sudo apt-get install asunder
```

---

### Post by bouncingwilf on 2010-08-01
Sadly, restoring asunder is not the issue - that's easily done ( but pointless unless I can find some way of navigating it to read from the USB drive) The main issue is that "places" is broken - I suspect that if I remove the taskbar and re-install all will be well but I've forgotten how!

Bouncingwilf

---

### Post by Greg_Brown on 2011-02-13
Hi.  I'm having the same issue.  Did you ever resolve it?  Thanks.

With a bit more searching I found this thread.  
[http://ubuntuforums.org/showthread.php?t=1352582&highlight=restore+places](http://ubuntuforums.org/showthread.php?t=1352582&highlight=restore+places)
The simplest solution is to reset the to File Manager the associations.

---

