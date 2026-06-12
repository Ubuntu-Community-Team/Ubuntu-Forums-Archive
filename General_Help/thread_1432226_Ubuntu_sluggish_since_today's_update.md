---
title: "Ubuntu sluggish since today's update"
date: 2010-03-17
forum: General Help
---

### Post by sideburns on 2010-03-17
My sister uses the most recent version of Ubuntu, and I'm her tech support.  (I use Fedora, personally, but it's way too geeky for her.)  Recently, she told me that her system was acting a bit unstable and programs were crashing.  Before I had time to look into it, she had a system update this morning, requiring a reboot.  Now, it's considerably less responsive, and Package Manager won't accept her password.  I tried opening a terminal to run top and see what's going on, but the window never opened.  Ctrl-Alt-Fn should switch me to a different virtual terminal, but doesn't.  Except for rebooting into the previous kernel, does anybody have a suggestion?

---

### Post by sideburns on 2010-03-17
More data: the system got so sluggish that it wouldn't respond to almost anything.  Finally, we were forced to reboot, one of the few things it did respond to.  The first time we rebooted, it hung, half-way through; the second time, it came up properly and the issue with the password seems to be cleared up for the moment.  I've had her install bleachbit, and will use it to clean things up, later.  If anybody has any suggestions for figuring out what happened, or how to keep it from happening again, I'd appreciate it.

---

### Post by PC_load_letter on 2010-03-17
Which kernel, or which update? I'm working with the latest version here, just updated last night to kernel 2.6.31-20, and everything is fine. 
If indeed the kernel update is the one that put you in trouble, why don't you choose the older version from the boot menu? Then you may want to read the system logs and see what caused the crash.

---

### Post by sideburns on 2010-03-17
She updated this morning, so it's the latest kernel.  And, it was already a tad unstable before the update, so it's probably not the new kernel, although it's possible that it made the issue worse.

---

### Post by mkvnmtr on 2010-03-17
Did she reboot after the update? That is required after installing a new kernel.I suppose running all day without rebooting could cause some problems. I think I would reboot two or three times and if that does not solve your problem lyou will have to dig a little deeper.

---

### Post by sideburns on 2010-03-17
Update manager told her to reboot, so she did.  However, I'd like to point out that we're talking about Linux here, not Windows; it doesn't require constant rebooting.  Here, we reboot only for kernel updates and shut down only for hardware issues or power failures.  Otherwise, our Linux boxen stay up 24/7, running BOINC.  Right now, my uptime is 33 days, and my Fedora 11 box is running just fine, TYVM.  And, she was having trouble with program crashes BEFORE the update, so I really doubt the new kernel is the issue.

---

### Post by PC_load_letter on 2010-03-18
There is nothing much anyone here can say to help without more specific information. At the end of the day, albeit you're using Fedora or Ubuntu, it's all Linux! Another thing to keep in mind is that this could be related to some hardware failure and has nothing to do with Ubuntu or any updates. Here are a few ideas:

- Boot with an older kernel, and/or in recovery mode and see if the problem is till there. 

- Boot the system with a Live CD, either Ubuntu or Fedora since you're more familiar with that, maybe you can run some diagnostics and check the hardware.

- If push comes to shove, there is always the backup + re-install routine. You can back up the files to an external drive while running the Live CD.

Hope this helps.

---

### Post by sideburns on 2010-03-18
You keep insisting that it must be the new kernel, even though I've repeatedly pointed out that it was unstable before the update.  Is there a log that goes back far enough that might suggest something?  If so, I'll give it a grovel and see what it says.

---

### Post by bandros on 2010-03-18
If this was my machine I would suggest running some routine hardware checks just to make sure you don't have a failing drive and that it is an actual OS issue at hand.  Try running disk checks from within the GUI or maybe an FSCK from virtual console.

---

### Post by sideburns on 2010-03-18
Thanx.  IIRC, there's some sort of hardware tester under System->Administration.  Which disk tests do you think it needs?

---

### Post by l4zy on 2010-03-18
Maybe you should also check apt-get / dpkg log's if the install has failed. If so i would reboot to recovery console and try to solve depencies. After that purge the newest kernel reboot. Install it again.. 

Also due apt-get you have good logs which packages has been installed during the last update, so i would check those packages, maybe even downgrade them to the older version and try that update again. 

Since if the box crashed before update/upgrade was finished, there might be bad installed packages or even corrupted files.

---

### Post by bandros on 2010-03-18
I would run fsck from terminal just to play it safe.  It will scan for any OS issues and try to fix or recover them if needed.  You can do this in any terminal windows, or virtual console.  Also, another test I would run is to see if the kernel in recovery mode has the same issue.  

Have you checked System Monitor to see if the swap file is low by any means.  Just basic tests nothing too advanced at the moment.  These are just basic things I would check before going any further.

---

### Post by sideburns on 2010-03-18
There's no need to check for failed updates for two reasons: first, because it didn't hang until after the reboot.  Second, for the fifth time, IT WAS UNSTABLE BEFORE THE UPDATE, SO THE UPDATE DIDN'T CAUSE THE ISSUE.  If you can't suggest something that doesn't assume that the update's the cause, don't bother posting.  Ignore the update and try to come up with things (such as a disk issue) that might have been causing the instability.

---

### Post by john newbuntu on 2010-03-18
Right sideburns.  Sluggish response, password not accepted, windows (including virtual terminals) not opening are not good signs.  As you suggested, do a smart check on the disk and also test memory thoroughly to rule out basic hardware issues there.  Follow this up with fsck using liveCD.  Check swap. When running apps, monitor htop or top to see the culprit.  Sorry could'nt point out the exact culprit here just things to do.

---

### Post by sideburns on 2010-03-18
Thank you, John, for reading my posts and responding to what I posted, instead of what any preconceptions you might have had made you expect.  I'll take care of that, starting tomorrow.

---

### Post by Zayfox on 2010-03-18
> **sideburns said:**
> There's no need to check for failed updates for two reasons: first, because it didn't hang until after the reboot.  Second, for the fifth time, IT WAS UNSTABLE BEFORE THE UPDATE, SO THE UPDATE DIDN'T CAUSE THE ISSUE.  If you can't suggest something that doesn't assume that the update's the cause, don't bother posting.  Ignore the update and try to come up with things (such as a disk issue) that might have been causing the instability.
The update could've made it worse.

---

### Post by Shadowangel21 on 2010-03-18
Hello geeks!, first let me introduce myself, im mark 21/ph installed ubuntu last week via windows based installer 'wubi'. Its been my hobby to install latest security updates such as kernel and make my system stable. I recently installed the latest kernel via update manager, after the system ask for reboot for the update to work, it says an error: you need to load the kernel first. 
Now i need help on how to load the kernel, although i can load my previous ubuntu kernel.

I need your help please.

---

### Post by lotharmat on 2010-03-18
> **Shadowangel21 said:**
> Hello geeks!, first let me introduce myself, im mark 21/ph installed ubuntu last week via windows based installer 'wubi'. Its been my hobby to install latest security updates such as kernel and make my system stable. I recently installed the latest kernel via update manager, after the system ask for reboot for the update to work, it says an error: you need to load the kernel first. 
Now i need help on how to load the kernel, although i can load my previous ubuntu kernel.

I need your help please.

Please start a new thread with this problem - It will help people not confuse the two different issues and you will more likely get the solution.

Cheers.

---

### Post by Shadowangel21 on 2010-03-18
> **lotharmat said:**
> Please start a new thread with this problem - It will help people not confuse the two different issues and you will more likely get the solution.

Cheers.

Yeah, sorry about that, i just thought of a quick solution thats why didn't created a new thread.

---

### Post by lotharmat on 2010-03-18
Always better to start a new thread  - It'll also help people if they come up against the same issue.

---

### Post by lordskid on 2010-03-18
I did experience a sluggish laptop after the updates. All I did was to reboot a second time and everything is back to normal.

I experienced worse in my netbook where after rebooting the first time the new kernel won't boot. I rebooted again and tried the same kernel and all is well now. 

So I want to suggest for you to try and reboot one more time. it might do the trick for you as well.

---

### Post by PC_load_letter on 2010-03-18
To the OP:
Could you open a terminal and post the output of:```
$htop
```
If it's not installed then install by```
$sudo apt-get install htop
```

---

### Post by sideburns on 2010-03-18
Just after the update, when things reached their worst, I tried that.  As reported above, the terminal window wouldn't open.  Now, however, the box seems to be doing OK again.

---

