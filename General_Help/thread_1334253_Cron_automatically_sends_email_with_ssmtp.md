---
title: "Cron automatically sends email with ssmtp?"
date: 2009-11-22
forum: General Help
---

### Post by paal on 2009-11-22
I've just added a cronjob to my crontab:
```
0 * * * * wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O /home/paal/.gnome2/world.jpg
```

Every time it's executed I receive a e-mail in my gmail inbox from their mailer daemon, saying that sending a email to [my ubuntu username]@[my computer name] has failed. It the message body is the text result from the cronjob. I have installed ssmtp and configured it to use my gmail account so I suspect that this has something to do with that.
How do I stop these mails?

---

### Post by phillw on 2009-11-22
you need to direct the output to /dev/null.   A quick HowTo is over here -->  [http://virtuelvis.com/archives/2005/04/script-output-bitbucket](http://virtuelvis.com/archives/2005/04/script-output-bitbucket)

Regards,

Phill.

---

### Post by dcstar on 2009-11-23
> **paal said:**
> I've just added a cronjob to my crontab:
```
0 * * * * wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O /home/paal/.gnome2/world.jpg
```

Every time it's executed I receive a e-mail in my gmail inbox from their mailer daemon, saying that sending a email to [my ubuntu username]@[my computer name] has failed. It the message body is the text result from the cronjob. I have installed ssmtp and configured it to use my gmail account so I suspect that this has something to do with that.
How do I stop these mails?

Install the **mailx** package.

---

