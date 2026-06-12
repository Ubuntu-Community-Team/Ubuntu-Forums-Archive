---
title: "computer running 9.10 crashing and stuff"
date: 2009-12-19
forum: General Help
---

### Post by a cup of tea on 2009-12-19
I am running Ubuntu on two computers. One is happy as a clam. The other is...well, having some problems, and I am not sure what I ought to be doing right now to deal with this.

A couple of days ago, while doing routine updates on that computer, there were some errors. I don't remember what. I wasn't able to click on things so I ctrl-alt-f1'd and rebooted from the console. It wouldn't boot. I then started the computer from a live CD, fsck'd it and fixed some errors. After that it booted again, said I had some broken packages (which I fixed) and it seemed like everything was doing fine afterward. 

Until...today. A few minutes ago it just froze for seemingly no reason. I couldn't even get to a console. I held down the power button to shut it off, restarted it, and it seems like everything's fine. I kinda doubt everything's fine. I'll fsck it again after I move some files off it (which I'm doing currently). I want to know what happened when it froze. I know there's a log I should be looking at...don't remember what though.

---

### Post by john newbuntu on 2009-12-19
The logs are located in /var/log/ directory.  If you know the time at which it froze, look up files that start with syslog, messages, kern.log, dmesg, Xorg etc for any errors.
I would also suggest checking the health of your hard disk drive using the Palimpset disk utility in system->admin->disk utility. Then click on more info on the right and conduct an extensive self test.  The more bad sectors you have, the more problems you are likely to encounter.  fsck or esfsck do not check disks.  They only check the consistency of the files in your system.

---

