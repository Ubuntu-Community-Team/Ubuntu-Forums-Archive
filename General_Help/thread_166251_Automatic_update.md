---
title: "Automatic update"
date: 2006-04-26
forum: General Help
---

### Post by henriette_holm on 2006-04-26
Hi.
I'm trying to get my computer to run apt-get automatically once a day. I'm trying to do this using cron but nothing happends. I type:

$ sudo crontab -e

and enter

35 10 * * * /usr/bin/apt-get --assume-yes update
40 10 * * * /usr/bin/apt-get --assume-yes upgrade

Anyone?

-Henriette

---

### Post by henriette_holm on 2006-04-26
Ok, small update.
It seems that the update runs but the upgrade doesn't.
Anyone?

---

### Post by strider1551 on 2006-04-26
Is --assume-yes a valid option?  I normally just use -y

My crontab is set up like this:
```

00 12 * * * sudo apt-get -qq -y update
01 12 * * * sudo apt-get -qq -y dist-upgrade

```

There are still some issues, though.  I guess some updates get confused if you have an edited config file (see [here]("http://ubuntuforums.org/showthread.php?t=102927")).

Dapper is supposed to support automatic updates from the manager (see [here]("http://www.ubuntuforums.org/showthread.php?t=159682")).

---

