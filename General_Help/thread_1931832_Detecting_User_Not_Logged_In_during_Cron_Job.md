---
title: "Detecting User Not Logged In during Cron Job"
date: 2012-02-26
forum: General Help
---

### Post by Kissell on 2012-02-26
I have a script that runs as root using cron.

And I have an event I only want to run if a user is logged in...

Is there a way I can detect this?

The system boots to the login screen and does not automatically login a user...  if it is as the login screen I do not want this event to run...  but if a user is logged in I need this event to run...  so I need a way to detect if ANY user is logged in.

Is there such a thing?

---

### Post by slugmax on 2012-02-26
(Assuming this is a shell script) 'who' will tell you who is currently logged in, with one entry per line. So

```

who | wc -l

```

Will return the number of users, or 0 if none are logged in.

```

loggedin=$(who | wc -l)
if [ "$loggedin" -gt "0" ]; then
    # code for when any users are logged in here
fi

```

If you just want non-root users, you can filter the output of 'who' so it excludes any root logins, like

```

who | grep -v root | wc -l

```

---

### Post by Kissell on 2012-02-26
Thanks!  I completely forgot about "who"

hmm.. for my usage I think I'll need to exclude any sftp or ssh connections and only care about the main keyboard/monitor/mouse.  This should do it.

> 
who |grep "(:0)"


---

