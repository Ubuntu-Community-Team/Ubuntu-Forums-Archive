---
title: "localhost mail for user and root?"
date: 2011-02-06
forum: General Help
---

### Post by ianc1 on 2011-02-06
I have recently discovered the existence of the localhost mail and found a number of messages for me.  I have a few queries regarding this.

I am looking at the users mail on localhost in Thunderbird.  After Thunderbird has downloaded the messages they are gone from the /var/mail/user file.  Is there any way to force Thunderbird to leave them there?

Also I see a number of posts suggesting forwarding the roots mail eg [http://ubuntuforums.org/showthread.php?t=7321](http://ubuntuforums.org/showthread.php?t=7321).  I appear to have no root email in 10.10 ie /var/mail/root doesn't exist.  Is this normal?  The user, me, only had 4 messages from failed cron jobs.

Finally in the above mentioned post are the following actions safe?```

sudo cp root username
sudo chown username username
sudo chgrp username mail
sudo gedit /root/.forward
```

I've just noted that the messages to me from the Cron Daemon all say they're from root@mypc.  Does this mean roots messages are being forwarded to me?

Thanks

---

### Post by ianc1 on 2011-02-09
Anybody any ideas?

I've looked in the /var/mail/mail file and all messages are from rkhunter on a daily cron job and all addressed to root@localhost.

Checking the config file for the rkhunter daily cron job reveals the messages are indeed sent to root@localhost.  Finally I've checked the /etc/aliases file and all the aliases bar mailer-daemon: postmaster are to root.

Therefore I am confused.  Why do I have a /var/mail/mail file and not a /var/mail/root file?  And why does "mail root" not pick these messages up?

Any ideas/explanations would be greatly appreciated as this is driving me nuts.

---

