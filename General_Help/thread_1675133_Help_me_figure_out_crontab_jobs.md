---
title: "Help me figure out crontab jobs"
date: 2011-01-25
forum: General Help
---

### Post by Maheriano on 2011-01-25
I'm looking into this but the websites I'm looking at aren't making as much sense as I think I can get here in way less time.

I'm looking at accessing a MySQL database to check a date of an entry and seeing if it's 15 days before today. If so I need to send a customized email to the email address in the same row.

If I set up a crontab job to check this daily, would I write a cron script to do all that or would I create it all in a PHP file and have the crontab manager simply run the file?

I've seen both online I think.

---

### Post by Cheesehead on 2011-01-25
You do it however will be easiest for you to maintain.

Myself, I would have cron trigger a separate script. Long, ugly crontab lines are harder for me to maintain and debug.

---

### Post by hawkmage on 2011-01-25
Creating a script and then running the script from cron is the easiest way of doing this.  One thing to keep in mind is that when cron runs something the PATH variable is either very limited or not set so I like to set the path in the script and/or use fully qualified paths to executables.

---

### Post by SeijiSensei on 2011-01-25
There are shell commands that allow you to access the database from a bash script, but I'd write it in PHP if you're comfortable with that. I've run a number of PHP scripts from crontab to take advantage of the wide array of functions already built into the language.  You'll need to install the php5-cli package if it's not there already, then just create crontab entries of the form:

```
01 00 * * * /usr/bin/php /path/to/script.php
```

---

### Post by blueridgedog on 2011-01-25
As a rule, I write and debug the functioning part of a job (in this case the script that will do the work) independent of the "scheduling" part of a job.

When you have a script (an any language that suits you) that works, getting it called by cron will be the easy part.

You may even want to do this within mysql as a stored procedure:

[http://dev.mysql.com/tech-resources/articles/mysql-storedprocedures.html](http://dev.mysql.com/tech-resources/articles/mysql-storedprocedures.html)

---

