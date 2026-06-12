---
title: "Can't load Ubuntu....screen goes black PLEASE HELP!!!"
date: 2009-10-09
forum: General Help
---

### Post by hapkidoman on 2009-10-09
A couple of days ago I installed updates to Ubuntu 9.10 Beta it stated that a system restart was necessary.  I shut down the computer but then had to switch over to Vista to do some other work.  Now today, I go back into Ubuntu 9.10 Beta and instead of loading to the splash screen, I get this error:

[7.300532] acerhdf: unknown (unsupported) BIOS Version Gateway/W3653/V1.12E, please report, aborting!

it then says: /dev/sda3 has been mounted 34 times without being checked, check forced.

It then does nothing....no noticeable check occurs.  I googled the problem and came across this [HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435958[/HTML], but it seems that people are still able to load just fine even with the error.  I wait for a minute and the screen is still black....nothing seems to be occuring.

Does anybody have any idea how I can get back into Ubuntu in order to install any (hopefully) updates that might address this problem?

---

### Post by hapkidoman on 2009-10-09
Is there anybody in there.....is there anybody home?

---

### Post by QIII on 2009-10-09
Please do not bump a thread so soon.  Remember that we are all here voluntarily and provide help as we have time.

According to launchpad, a fix was made available half an hour ago (from the time I am typing this).

If you can drop to the command line from the recovery option, try to apt-get update and apt-get upgrade.

And remember that a Beta is a Beta.  You are bound to encounter errors like this until at least the Release Candidate.

---

### Post by hapkidoman on 2009-10-09
Very true.  I did eventually get it to work.  Hopefully the new updates will fix the problem so that others won't have the same problem.  

Thanks for the help

---

