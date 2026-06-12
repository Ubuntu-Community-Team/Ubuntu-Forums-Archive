---
title: "MAILTO doesn't do anything"
date: 2009-11-16
forum: General Help
---

### Post by provoko on 2009-11-16
Hi.  I'm trying to send e-mails from cron to my e-mail address with the MAILTO environment, but it's not working.  I'm running x86 ubuntu 9.04.

First I had to set the MAILTO with export MAILTO=fake@gmail.com
But then it wouldn't stick so I updated my .bashrc with export MAILTO=fake@gmail.com
Then I used crontab -e and typed:

SHELL=/bin/bash
MAILTO=fake
30 6 * * * /sbin/ifconfig

But I get nothing in the mail, even when I set it for 5 minutes in the future.  What's the problem?  Should I just put my e-mail address in cron?  Is something wrong with ifconfig?

Thanks for any advice.

---

### Post by provoko on 2009-11-17
Maybe I should ask a better question: How do I set up my e-mail address on linux so that programs or scripts can send me mail when I call on an envirnment like MAILTO?
 
Thank you.

---

