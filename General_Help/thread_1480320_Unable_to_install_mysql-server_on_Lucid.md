---
title: "Unable to install mysql-server on Lucid"
date: 2010-05-11
forum: General Help
---

### Post by rrwo on 2010-05-11
I've tried installing mysql-server on Lucid, and I get errors that it cannot set the root password. A screenshot is attached.

I have no idea what to do. I've tried purging configuring and reinstalling. Same problem. I can't find anything in the logs.

---

### Post by lewac on 2010-05-11
yes I have something similar. that referenced user.frm file isn't found anywhere on my sys after the install. I also have no clue where to turn here. can't set mysql server root pw and in fact I can't get a connect no how! the dumbrections indicate that after install root is blank pw so why no connect? this is a fresh install of mysql on i386 32 bit so obviously its makes no diff what cpu and bit size our machines are running. I've tried launching "MySQL Administrator" via the gui and I get the attached error. it doesn't matter whether I launch from the menu or the CLI under sudo. same problem (and I'd prefer not having to use sudo for this).

---

### Post by rrwo on 2010-05-17
This was apparently due to my configuration file /etc/mysql/my.cnf missing.

---

