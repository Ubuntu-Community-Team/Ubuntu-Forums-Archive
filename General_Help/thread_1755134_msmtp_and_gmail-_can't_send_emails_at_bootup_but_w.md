---
title: "msmtp and gmail- can't send emails at bootup but works after login"
date: 2011-05-10
forum: General Help
---

### Post by drnick79 on 2011-05-10
Hi all,

I'm running 11.04 desktop 64 bit and have smartmontools and mdadm set to send automated test emails at bootup (I have a RAID5 setup). 

I'm using msmtp with a gmail account. When I'm logged in, I can manually send test emails with both smartmontools and mdadm; neither will send me an email at bootup even though they are set to do so. The msmtp log at bootup has a smtp.gmail.com exitcode=EX_NOHOST.

Any ideas why it can't find the smtp server at bootup but has no problem once I'm logged in and test it manually? Is there some dependency that isn't loading in time at bootup???

Thanks for any info!

---

### Post by drnick79 on 2011-05-13
I noticed now that I will sometimes receive test emails from the smartmontools and/or the mdadm daemons at bootup, even though I haven't changed any mail or monitoring parameters. However, there are still times when I power on/restart the computer and no test emails are sent. 

Any ideas as to why the test emails aren't sent consistently at bootup, but will consistently be sent when I manually send them using the appropriate commands in the terminal???

---

