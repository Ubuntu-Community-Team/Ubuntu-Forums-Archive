---
title: "How can I verify my server is getting security updates correctly?"
date: 2012-01-14
forum: General Help
---

### Post by tbharber on 2012-01-14
I have an Ubuntu 11.04 server setup and during install I selected the option to automatically update my server.  My question is how can I verify it is being updated correctly?  

In the desktop version I know where to go to update my system, but with the command based server how can you do this?  Being that there is no GUI I would assume there is a log of some kind of what is being updated.

Any thoughts?

---

### Post by spacecheck on 2012-01-14
Up front: I've never installed nor updated the server.

I suspect you would nonetheless be able to call up the updates with
```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```The relevant log files may possibly  be found in /var/log/apt
Again, I've never installed nor updated the server, so thake that with several grains of salt...

I'm sure there are several places you can find the definitive information, though, if you search properly.

I found this recent post:
[http://ubuntuforums.org/showthread.php?t=1895084](http://ubuntuforums.org/showthread.php?t=1895084)

Item 3 points to updating. To be sure, automatic updates on a server are to be enjoyed with a heavy side order of concern.

Good luck!

---

