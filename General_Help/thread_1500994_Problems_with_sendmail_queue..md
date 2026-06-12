---
title: "Problems with sendmail queue."
date: 2010-06-03
forum: General Help
---

### Post by xonev on 2010-06-03
I have been having trouble with Ubuntu's sendmail configuration.  Specifically, I want to delete all of the messages in the queue.  I've been able to delete the files which I *thought* were representing the queue in /var/spool/mqueue, but though this helps, it seems like there is a cron script running that causes the queue to be repopulated with the messages I don't want to send.  I think the command line which is running is this: ```
test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp
```

What does that do?  Is it my problem?

More information here [http://serverfault.com/questions/147676/how-do-i-permanently-delete-e-mail-messages-in-the-sendmail-queue-and-keep-them-f]("http://serverfault.com/questions/147676/how-do-i-permanently-delete-e-mail-messages-in-the-sendmail-queue-and-keep-them-f")

---

