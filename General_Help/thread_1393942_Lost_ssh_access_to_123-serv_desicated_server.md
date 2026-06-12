---
title: "Lost ssh access to 123-serv desicated server"
date: 2010-01-29
forum: General Help
---

### Post by innerspaceproductions on 2010-01-29
My company purchased a dedicated server from 123-reg.co.uk and first glance of the bespoke control panel had me shocked at how little control it had.

Needing cron jobs and a whole heap of other features this left us no choice but to request root access and waive their technical support.

After getting the password I SSH'd in which worked fine.

I installed virtualmin, which again worked fine.

I hit an error with the mysql password, which I managed to change to something that I knew but still was unable to get virtualmin to recognise. 
It kept coming up with an access denied on root@localhost: (using password: no) - event though I was telling it the root password.

At this stage I decided to remove all the software and setting installed by 123-reg and start again, letting virtualmin setup a fresh installation. 
Yet before I could try the problems started.

Trying to reopen an SSH session I kept hitting a request refused error. I tried a couple of different SSH clients all with the same problem.

At this time I was still connected to virtualmin and could control the system from terminal.

I tried a reboot and that left me with no SSH, webmin or virtualmin access.
Yet annoyingly I could still access the useless 123reg control.

But the strangest thing is that after trying everything I could think of, I started writing this post - started an SSH connect so that I could write the exact error message - and it worked!

Does anyone have any suggestions as to the possible cause of these events in case they occur again?

Just glad I have access again, wasnt't looking forward to the possibility of being charged for an OS install days after purchase, but without access or support few options would be left.

---

### Post by innerspaceproductions on 2010-01-30
It has all been progressing well since I started writing the previous message.

I have gained SSH access and removed unnecessary software.

After removing apache I checked the 123-control panel and it was still working, so following the advice on this thread I broke out of jail and accessed the true root.

[http://ubuntuforums.org/showthread.php?t=708617&highlight=123serv&page=2](http://ubuntuforums.org/showthread.php?t=708617&highlight=123serv&page=2)

Viewing the ssh config file this is listening on a non-standard port xxx
The ssh config in the jail is listening on 22

Checking netstat says that ssh is listening on 22 and xxx

I would presume that this would allow me to ssh directly into the true root using port xxx but this is giving me timeout errors.

Any ideas whats wrong?

Also how could I remove the chroot jail once I have broken out?

---

