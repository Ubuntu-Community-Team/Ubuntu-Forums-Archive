---
title: "Auto-shutdown script"
date: 2011-01-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-01-13
Is there a way I can set the computer to shut down after 1 hour is no one has logged in?
My sister/dad will turn it on to print and not turn it off after.

---

### Post by Crusty Old Fart on 2011-01-15
There might be a better way to do it than what I've come up with here. But, if there is, then I don't know about it.

The following method won't shut down the computer in exactly one hour if no one is logged on. But it might get you a lot closer to what you want to do than anything else. It'll hit the target somewhere between about 30 minutes and an hour.

So, here's the deal. The first thing to do is make a small sleeper script that will allow the computer to run without anyone logged on for 29 minutes. Unless someone logs on for more than a minute during that time, the script will wake up and check for a user every minute. If it finds a user, then the script will terminate. If it runs for the full 29 minutes without a user logging on, then the script will shut down the computer. The code in this post assumes the script is stored in your home directory: /home/your_name
For this example, we'll name the script: no_users
Here it is:
```

#!/bin/bash
while [[ ! $(users) =~ .+ ]]; do 
  sleep 1m
  (( timeout = $timeout + 1 ))
  (( $timeout >= 29 )) && shutdown -P now
done
exit 0

```Now we need a way to run /home/your_name/no_user every thirty minutes whether or not any users are logged on. For this, we need to create a file as root in /etc/cron.d
For this example, we'll name the file: user_check
Here's the code to put in /etc/cron.d/user_check
```


SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

0,30 * * * * root /home/your_name/no_users


```That's all there is to it.

The cron code in /etc/cron.d/user_check will run /home/your_name/no_users at the top and bottom of every hour.

The longest amount of time your computer will remain on without anyone logged in will be about 59 minutes. This will happen if the cron code launches the script shortly BEFORE they log off because the script will find them using the machine and will terminate until it is launched again by the cron code, 30 minutes later. The script will then have to run for another 29 minutes without finding a user before it will shut down the computer.

The shortest amount of time your computer will remain on, after someone logs off will be 29 minutes. This will happen if the cron code launches the script shortly AFTER they log off.

You may want to play around with the numbers to suit your needs a little better. Just be careful not to do anything goofy to yourself like the dirty trick of setting the cron code to run every two minutes and your script to time out in 45 seconds. If you do that, like I did to speed up my testing, you might have one helluva panic trying to log back in again before it shuts down on you :cool:

Happy to answer any questions.

Good Luck,

Crusty

---

### Post by pqwoerituytrueiwoq on 2011-01-15
thanks i will try put this into play when i get home in a few days
does it matter where i put no_users? (assuming i keep the location correct)
for example the opt folder or root's home folder

---

### Post by Crusty Old Fart on 2011-01-15
> **pqwoerituytrueiwoq said:**
> thanks i will try put this into play when i get home in a few days
does it matter where i put no_users? (assuming i keep the location correct)
for example the opt folder or root's home folder
Nope. You can put the **no_users** script [COLOR=Blue]**/on/the/moon**[/COLOR] if you want. There's nothing special about the name: **no_users** either. You could name it: [COLOR=Green]**anything**[/COLOR]. The main thing you have to be sure of is that you specify the full path to the script in the file named: **user_check** that contains the cron code, as follows:
```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

0,30 * * * * root [COLOR=Blue]**/on/the/moon/**[/COLOR][COLOR=Green]**anything**[/COLOR]
```There's nothing special about the file containing the cron code being named: **user_check**. You could name it: [COLOR=Blue]**whatever**[/COLOR]. However, the file containing the cron code [COLOR=Red]_**must**_[/COLOR] be created as root inside the [COLOR=Red]**/etc/cron.d**[/COLOR] directory. As in: [COLOR=Red]**/etc/cron.d/**[/COLOR][COLOR=Blue]**whatever**[/COLOR]

---

