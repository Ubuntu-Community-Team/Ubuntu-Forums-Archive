---
title: "Permission denied--failed upgrade, missed some backup data, can see it but not get it"
date: 2010-05-15
forum: General Help
---

### Post by ysaric on 2010-05-15
I tried a 9.10 -> 10.04 upgrade that went fail.  I can now get it to the login screen where it gives  a hard freeze.  Same with recovery.  I can get to a command line, but not with networking so

So I finally said screw it, I'm going to doa fresh install.  I downloaded and burned 10.04 at work.  Not, it is giving me an installer error when I boot from it, but then it will load the desktop from the LiveCD.

All I really want to do is grab some data that I didn't get when I backed up by home directory, then I can go back and do a fresh install.  I can even download a new 10.04 CD if I need to because the installation files are screwed up or something.

The problem is that some of the files have permissions on that that show as an 'X' on the icon and it won't let me copy them to my USB backup drive.

How can I copy the files marked with an 'X' that have this permission issue?

Any help or advice would be greatly appreciated.

---

### Post by ysaric on 2010-05-15
Dunno if 10 hours is too soon to bump, but I am hoping to be able to resolve this yet this weekend.  Thanks again in advance for any advice or information provided.  I am pretty good with finding and editing files or locating logs, if any additional information would be useful, please let me know.

---

### Post by ba_saish on 2010-05-16
did you try using the terminal to copy? use sudo with the cp command and try.

---

### Post by ysaric on 2010-05-17
> **ba_saish said:**
> did you try using the terminal to copy? use sudo with the cp command and try.

Yup actually I went back and tried that and it worked.

Fresh install of 10.04 worked, too.

Thanks much for the reply.

---

