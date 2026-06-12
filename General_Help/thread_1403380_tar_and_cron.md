---
title: "tar and cron"
date: 2010-02-10
forum: General Help
---

### Post by w1ski on 2010-02-10
Ubuntu 9.10 with all upgrades.  I am using a script to run with cron to back up some files to just tar them and tar does not work correctly.  When I manually run the script, it works fine and I get a good back up.  When I run it under cron, tar exits with the error:  tar: unexpected EOF in Archive with out completing the back up.  When I untar or extract the files I see two lines with the above error.  Looks like it happens in the Thunderbird directory.

I have tried several different scripts with the same results on a desktop and a laptop.  Any ideas?

---

### Post by gmargo on 2010-02-10
Please post a simple script that demonstrates the problem.

---

### Post by falconindy on 2010-02-10
Post your crontab as well.

---

### Post by SecretCode on 2010-02-10
cron runs jobs as the root account, I believe. Do you have any paths relative to your home directory? Do you have any archives not readable by root?

---

