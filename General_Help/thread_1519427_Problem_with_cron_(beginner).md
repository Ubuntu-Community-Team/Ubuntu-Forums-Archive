---
title: "Problem with cron (beginner)"
date: 2010-06-28
forum: General Help
---

### Post by shinokada on 2010-06-28
My work's server is running on Ubuntu.
I used WinSCP (and Putty) to connect and set up the crontab.

```
*/10 * * * * /usr/bin/wget http://moodle.mywork.org/admin/cron.php
```

However when I run, wget [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php) on Putty, it shows Connecting to moodle.mywork.org|81.167..bla bla

for 20 times and at the end it say giving up.

What do I need to run properly?

Thanks in advance.

---

### Post by Ryan Dwyer on 2010-06-28
Is moodle.mywork.org hosted in your local network? If so, you need to add an entry in /etc/hosts to make it resolve to the private IP instead of the public IP address.

---

### Post by yeleek on 2010-06-28
Always confirm before you run something as cron that it works for you

```
wget [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php)
```

Does that work?  

Even if it does, you don't seem to be telling wget/cron where to put those files?

---

### Post by shinokada on 2010-06-29
When I run wget [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php), it tries 20 times (take more than 30min) and gives up.

When I visit [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php) on a browser, it runs cron.

Why is it and how can I fix it?

Thanks in advance.

---

### Post by yeleek on 2010-06-29
> **shinokada said:**
> When I run wget [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php), it tries 20 times and gives up.

When I visit [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php) on a browser, it runs cron.

Why is it and how can I fix it?

Thanks in advance.

What is it specifically you are actually trying to do?  Whats the desired end result.

---

### Post by shinokada on 2010-07-01
[http://docs.moodle.org/en/Cron#Using_a_cron_command_line_in_Unix](http://docs.moodle.org/en/Cron#Using_a_cron_command_line_in_Unix)

I need to do cronjob regularly to visit my school's webaddress. This http address will do things such as backing up courses, sending messages etc.

---

### Post by yeleek on 2010-07-05
OK well WGET can only download that page (can't create messages for you), and if the webpage itself requires authentication to logon with then you are going to need to include those logon credentials in your command line (or via cookie).

So...
1) Does the website require logon credentials to logon with?
2) Your original wget command 'wget [http://moodle.mywork.org/admin/cron.php](http://moodle.mywork.org/admin/cron.php)' isn't going to place those files anywhere in particular and isn't allowing for any timestamping (I presume the goal is to backup the site?)
[http://www.gnu.org/software/wget/manual/wget.html#Time_002dStamping](http://www.gnu.org/software/wget/manual/wget.html#Time_002dStamping)
3) You also need to consider is it a full backup of the site you want, or only specific files/images/domain names as this affects other options WGET provides.

Just looked at that link - see they are advising running it quite (-q) and providing a destination (-O).  However they are not running the wget itself in a local cron, so as I said you need to consider where you want these files...

---

