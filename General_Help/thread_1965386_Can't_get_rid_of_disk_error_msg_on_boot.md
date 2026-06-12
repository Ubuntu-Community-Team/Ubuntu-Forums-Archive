---
title: "Can't get rid of disk error msg on boot"
date: 2012-04-25
forum: General Help
---

### Post by Chrison999 on 2012-04-25
When I boot Ubuntu (10.04) I get an error message at the Ubuntu splash screen telling me there are disk errors on /boot (/dev/sda1) and /home (/dev/sda7).  I'm ask to enter "F" to fix, "C" to continue and so forth.  I always hit "F" and the drives are then checked and Ubuntu continues to boot normally.  However, when I boot the system the next time, I get the same error message on the same drives.  This is been going on for a couple of weeks now.

Today, I booted into recovery mode and dropped to a root terminal where I ran "fsck -f -v -c" on both drives but fsck didn't appear to discover any errors.  When I rebooted into regular mode, I got the same darned error messages again!  :(

Am I missing something here?  Am I running the wrong utility or using the wrong command switches?  This problem is beginning to get to me!

Thanks for any help/advice offered!

Regards,

Chris

---

### Post by latinlightning on 2012-04-25
If it's been going on for a couple of weeks then I would take advantage of the times that you are able to successfully boot into the operating system and back-up all important information that you don't want to lose. Then do an actual hard drive test such as the one provided from Seagate to check the integrity of your HD.

---

### Post by Gatorade on 2012-04-25
> **Chrison999 said:**
> When I boot Ubuntu (10.04) I get an error message at the Ubuntu splash screen telling me there are disk errors on /boot (/dev/sda1) and /home (/dev/sda7).  I'm ask to enter "F" to fix, "C" to continue and so forth.  I always hit "F" and the drives are then checked and Ubuntu continues to boot normally.  However, when I boot the system the next time, I get the same error message on the same drives.  This is been going on for a couple of weeks now.

Today, I booted into recovery mode and dropped to a root terminal where I ran "fsck -f -v -c" on both drives but fsck didn't appear to discover any errors.  When I rebooted into regular mode, I got the same darned error messages again!  :(

Am I missing something here?  Am I running the wrong utility or using the wrong command switches?  This problem is beginning to get to me!

Thanks for any help/advice offered!

Regards,

Chris


try this [http://gtatradingpost.freeforums.org/how-to-repair-mount-of-file-system-failed-error-t28.html]("http://gtatradingpost.freeforums.org/how-to-repair-mount-of-file-system-failed-error-t28.html")

it might work for you. if you can boot , you may not need to use the live cd.

---

### Post by Chrison999 on 2013-01-02
None of the suggestions offered above solved my problem.  Since this problem didn't seem to effect everything else with the computer, I just ignored it and kept clicking the "fix" option every time I booted the computer.

Then, yesterday, I was trying to fix another issue by booting into recovery mode when Ubuntu hung with an error message saying the "last update" for my drives was in the future.  Huh?!?!  So, I took a look at my BIOS settings and noticed that my BIOS clock was *way* off (January 2009)!  I'm not sure how that had happened and, obviously, Ubuntu was adjusting itself to the current date/time each time I booted (or else I would have noticed this sooner).

Anyway, I adjusted to BIOS clock to the current date and time and, voila!  Problem fixed!  I have rebooted the computer numerous times, just to see if the problem would reoccur but, so far, it hasn't.

Hope this helps anyone who's experiencing similar problems!  Thanks to everyone who offered their help, even though it didn't fix things.

Regards,

Chris

---

