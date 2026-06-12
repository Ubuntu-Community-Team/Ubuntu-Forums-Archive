---
title: "cron job not working"
date: 2011-01-11
forum: General Help
---

### Post by neokyle on 2011-01-11
Im useing crontab to execute a script in an sh file every 5 minutes. After 5 minutes nothing happens. i know the script works because i can manually run it.

This is the script.

#!/bin/bash
a=$(date)
cp -r "/home/neokyle/mcoriginal/cn/bin/world" "/home/neokyle/worldbackups/world$a"

any ideas?

---

### Post by CharlesA on 2011-01-11
Is your home directory encrypted?

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> Is your home directory encrypted?

no its not, i actually have another cron job that goes through the same path and it works just fine.

---

### Post by CharlesA on 2011-01-11
Try this:

```
#!/bin/bash
DATE=$(date)
cp -r /home/neokyle/mcoriginal/cn/bin/world "/home/neokyle/worldbackups/world${DATE}"
```

Only need quotes on the second one.

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> Try this:

```
#!/bin/bash
DATE=$(date)
cp -r /home/neokyle/mcoriginal/cn/bin/world "/home/neokyle/worldbackups/world${DATE}"
```

Only need quotes on the second one.

same result as when i first posted.

The script does work as it was, it only doesnt work as a cron job.

If it matters i have the script placed in /<root>

---

### Post by CharlesA on 2011-01-11
What does the crontab entry look like?

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> What does the crontab entry look like?

* * * * * ./copyscript.sh

it was */30 * * * * ./copyscript.sh

i change it to from */30 to * so i could see if it worked without having to wait 30 minutes.

---

### Post by CharlesA on 2011-01-11
That doesn't look right.

So the shell script is located on the root of the drive?

It should look something like this:

```
*/5 * * * * /path/to/script
```

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> That doesn't look right.

So the shell script is located on the root of the drive?

It should look something like this:

```
*/5 * * * * /path/to/script
```

the script is located in / , there is a folder in / called root. the crontab files are in root, the script (sh file) is in /

So your saying i should do */5 * * * * /

because copyscript.sh is located in / ???

---

### Post by CharlesA on 2011-01-11
Yes.

In your case it would look like this:

```
*/5 * * * * /copyscript.sh
```

---

### Post by neokyle on 2011-01-11
*/5 * * * * /copyscript.sh

Doesnt do anything :(

---

### Post by CharlesA on 2011-01-11
Try redirecting the output to a file like so:

```
*/5 * * * * /copyscript.sh > /home/neokyle/cronjob 2>&1
```

---

### Post by neokyle on 2011-01-11
*/5 * * * * /copyscript.sh > /home/neokyle/worldbackups/world 2>&1

the above did  not work.

---

### Post by CharlesA on 2011-01-11
It won't work like that.

You'd have to use the command in my previous post.

---

### Post by neokyle on 2011-01-11
when i enter

/copyscript.sh > /home/neokyle/worldbackups/world 2>&1

as a command in the terminal it says 

-bash: /home/neokyle/worldbackups/world: Is a directory

So you didnt want me to change the crontab, i should change it back to */5 * * * * /copyscript.sh ???

---

### Post by CharlesA on 2011-01-11
Put it the crontab exactly like this:

```
*/5 * * * * /copyscript.sh > /home/neokyle/cronjob 2>&1
```

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> Put it the crontab exactly like this:

```
*/5 * * * * /copyscript.sh > /home/neokyle/cronjob 2>&1
```

still nothing :(

---

### Post by CharlesA on 2011-01-11
Try putting this in a crontab:

```
*/1 * * * * touch /tmp/crontest
```

Check after a minute to see if the file is there.

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> Try putting this in a crontab:

```
*/1 * * * * touch /tmp/crontest
```

Check after a minute to see if the file is there.

no crontest directory made in /tmp/

---

### Post by CharlesA on 2011-01-11
It would have made a file.

Check to make sure cron is actually running.

```
service cron status
```

---

### Post by neokyle on 2011-01-11
> **CharlesA said:**
> It would have made a file.

Check to make sure cron is actually running.

```
service cron status
```

cron start/running, process 1915

---

### Post by neokyle on 2011-01-11
Problem solved

I put both crontabs into one file instead of having two crontab files. apparently it was only executing the first crontab that I made and not the second one which i had the problem with.

Now i know, put all crontabs in one file.

thank you for all the help charles :)

---

