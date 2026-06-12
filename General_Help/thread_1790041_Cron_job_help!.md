---
title: "Cron job help!"
date: 2011-06-24
forum: General Help
---

### Post by linuxgr on 2011-06-24
Hey guys,
I have been googling my issue with no luck. What I need is pretty simple actually, but I do not know if it can be done. I have set up a user account and I need to execute a script every 15 minutes but _only while the specific user is logged in_. I do not want it to run if the user is logged out.

Can I easily restrict cron in that way or do I need to check if the user is logged in from the script that runs? (e.g. if [ $(who | grep username) != 0 ] then.....)

thanks

---

### Post by CrusaderAD on 2011-06-24
I think you can setup the cron using this user with this:

```
crontab -e
```

This should set it up for this user only. Try that and see if it executes while not logged in.

```
sudo crontab -e
```

Would set one up for root.

---

### Post by linuxgr on 2011-06-24
That is exactly what I did thinking that I was setting up a job for when the user is logged in, but the job runs no matter what. For now I have added a check in my script to see if the user is logged in, but I would prefer to somehow do this through cron. (So i do not have to include the check in every script I want to use).

---

### Post by mike909 on 2011-06-24
So are you saying that if you 
> su - <user_name>
then execute
> crontab -e
and insert your command, it runs that cronjob regardless of which user is logged in?

---

### Post by MSPdwalt on 2011-06-24
Yes, that's the way cron works.  It executes job as the user who's crontab it's in at the specified time as long as the system is on and the cron daemon is running. You could do a login script that loops every 15 minutes instead.

---

### Post by Dave_L on 2011-06-24
Does the script need to run as root, or can it run as the specific user?  If the latter, you could put the script in ~/.config/autostart/, and it could look like this:

```
#!/bin/bash

while true; do

# do stuff
# ...

# wait 15 minutes
  sleep 15m

done
```

---

### Post by linuxgr on 2011-06-24
Thanks guys, that's more or less what I ended up doing. I actually put this on the top of the script:

```

if [ $(who|grep -c USERNAME) -eq 0 ]
then 
    exit 1
fi

```

And works just fine. I guess I'll just have to add this to all scripts.

Thanks all for the help!

---

### Post by MSPdwalt on 2011-06-24
Don't forget to mark this solved. ;)

---

### Post by DaithiF on 2011-06-25
> **linuxgr said:**
> I guess I'll just have to add this to all scripts.

Don't do that.  Create 1 script that checks if a user is logged in, and use that script in your cron entry.

e.g.
create a script called loggedin
```
#!/bin/bash
who | grep -q $1

```

then your cron entry:
```
* * * * * /path/to/loggedin dave && /path/to/commandtorun

```
if dave isn't logged in, then the 2nd command won't run

---

