---
title: "Unable to update or get new software"
date: 2011-12-16
forum: General Help
---

### Post by Costas100 on 2011-12-16
I just found a solution in thread: [http://ubuntuforums.org/showthread.php?t=1667761](http://ubuntuforums.org/showthread.php?t=1667761) very simple and works in seconds:
sudo rm /var/lib/apt/lists/lock
sudo touch /var/lib/apt/lists/lock
Thank you Fedor Biryukov
Now my problem is that I cannot cancel or delete this post. My apologies but the only thing I can do is "Submit New thread"

I am running on a fresh install of Ubuntu 10.10 (I had to reinstall it after some problems).
A new and serious problem appeared this morning:
When I tried to update (mostly security related software) I received a message that:
[INDENT]> Failed to lock the package manager
Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

Details
The package indexes are currently changed by apt-get.
[/INDENT]

I made absolutely sure that there were no other Synaptic open at the time and tried again and again allowing some time in between. I am not sure what : "The package indexes are currently changed by apt-get" means and how to solve this problem. 

Any suggestions will be greatly appreciated.

Costas

---

