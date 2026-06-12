---
title: "Problem running script from cron"
date: 2011-03-01
forum: General Help
---

### Post by MonkeyZiggurat on 2011-03-01
I still can't figure out why my cron job isn't working. I'm sure I'm missing something obvious, but it's got me beat:(

I know cron is executing my script (I had it echo some lines to a file at points within the script, and that text showed up, but none of the files/folders are being copied or removed)

crontab looks like this:

```

PATH=/usr/sbin:/usr/bin:/sbin/bin

#m h  dom mon dow   command

*/20 * * * * /scripts/scriptname

```

and the script itself like this:

```
#!/bin/bash



#-------------------------ALERT Email------------------------------

/usr/bin/find /home/xxx/from_xxx/ -type f -name ra_\* > /var/notifications/remitFiles

               if [ -s "/var/notifications/remitFiles" ]; then

echo "To: user@domain.com
From: root@domain.com
Subject: Remittance Data

There are new remittance files. They will be available for download in a minute or two.

This is an automated message, please do not reply to this address.

" > /var/notifications/remitEmail

                        ssmtp -t < /var/notifications/remitEmail
                        echo "email check done, email sent" > /var/notifications/INT.debug

                else

                echo "email check done, no email sent"  > /var/notifications/INT.debug

              fi

#--------------------------OUTGOING--------------------------------


/usr/bin/find /home/xxxtrans/to_xxx/DM -type f -exec cp {} /media/HDD2/ServerSpaceBackups/xxx/to_xxx/DM/ \; -exec cp {} /home/xxx/to_xxxx/DM/ \; -exec rm {} \;

/usr/bin/find /home/xxxtrans/to_xxx/DATA -type f -exec cp {} /media/HDD2/ServerSpaceBackups/xxx/to_xxx/DATA/ \; -exec cp {} /home/xxx/to_xxx/DATA/ \; -exec rm {} \;

#--------------------------INCOMING--------------------------------

/usr/bin/find /home/xxx/from_xxx/ -type f -name \*.txt -exec todos -ep {} \;
/usr/bin/find /home/xxx/from_xxx/ -maxdepth 1 ! -name from_xxx -type d -exec cp -r {} /media/HDD2/ServerSpaceBackups/xxx/from_xxx/ \; -exec cp -r {} /home/xxxtrans/from_xxx/ \; -exec rm -r {} \;
/usr/bin/find /home/xxx/from_xxx/ -maxdepth 1 -type f -exec cp {} /media/HDD2/ServerSpaceBackups/xxx/from_xxx/ \; -exec cp {} /home/xxxtrans/from_xxx/ \; -exec rm {} \;
```

I've replaced the username with xxx, but you get the idea.

Can't see anything wrong with the script itself, it isn't pretty but it works on the command line.

Thanks

Joe

---

### Post by laceration on 2011-03-01
It would be great if we had something in Linux would simply run a script that runs at the CLI.  I've been frustrated many times with Cron, it seems to bog down sometimes from complicated scripts, but I think the only explanation is that it just a mediocre program that often doesn't run well.  You can try rewriting your script, maybe if you approach it differently Cron will handle it or split it into multiple scripts + put them in multiple cron lines.  You think Cron works for you? -- No, you work for Cron!  There was a project to replace Cron, hopefully it will bear fruit soon.

---

### Post by artaxerxes on 2011-03-01
1. I don't know that this is related to your problem but I don't think that **/sbin/bin** is a real path. It is not on my system and does not look like anything with which I am familiar. Did you mean **/sbin:/bin** ? Of course if you have such a path then you should ignore this one.


2. More along the lines of things to look for:
    Are you getting any errors mailed output?

    Is your /var/notfications/remitfiles getting created ?

    Are your finds finding anything?
      (you might have to temporarily remove your actions and just let       find print the names to see what is happening)

Anyway,
I hope this helps get you pointed towards a solution.

---

### Post by gmargo on 2011-03-01
> **MonkeyZiggurat said:**
> I still can't figure out why my cron job isn't working. 
What error did you get from cron?  Check /var/log/syslog.  Check the email that the cron daemon sent you.

> 
```

PATH=/usr/sbin:/usr/bin:/sbin/bin

```If that "/sbin/bin" is not a mistake in copy/paste, then it's probably the source of your problem.  Leave out the PATH; let it default unless you need a non-standard directory.

---

### Post by MonkeyZiggurat on 2011-03-02
That's it!

> 1. I don't know that this is related to your problem but I don't think that /sbin/bin is a real path. It is not on my system and does not look like anything with which I am familiar. Did you mean /sbin:/bin ? Of course if you have such a path then you should ignore this one.
> If that "/sbin/bin" is not a mistake in copy/paste, then it's probably the source of your problem. Leave out the PATH; let it default unless you need a non-standard directory.

it should have been /sbin:/bin, but taking the whole line out completely hasn't done any harm and now my script is doing it's job.

Quite frustrating that cron didn't send me any kind of error message or even anything suspicious in syslog, considering that there's no such thing as /sbin/bin, but then again I guess I should have spotted that. :oops:

Thanks for the help!

Joe

---

### Post by gmargo on 2011-03-02
> **MonkeyZiggurat said:**
> 
Quite frustrating that cron didn't send me any kind of error message or even anything suspicious in syslog

Cron will send you email with any output or errors from the command.  You should have seen an error because the script could not find the "/bin/cp" command.

Check your syslog again.  Did you see a message from cron something like "MTA not found, output discarded"?  That was your error message.

---

