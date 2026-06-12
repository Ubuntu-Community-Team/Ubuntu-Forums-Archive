---
title: "crontab not running cnee command"
date: 2010-08-25
forum: General Help
---

### Post by abid_naqvi83 on 2010-08-25
I am running Ubuntu 9.10. I used cnee to record a session in which the mouse clicks on a tab on the bottom panel and presses a few buttons in a window before minimizing it. The session works perfectly when called from the terminal.

I then wrote a script titled task.sh:

```
#!/bin/bash

# Launces an xnee Sessin file.

echo "Program Executed" > /home/abid/.bin/output.txt
cnee --replay -f /home/abid/.bin/task.xnr --time 2
notify-send "Debug" "Program Ends"
```


The script also executes perfectly when called from the terminal. I then set about automating this task using crontab and edited it as follows:


```
# m h  dom mon dow   command
@hourly /home/abid/.bin/new_email.sh
44 4 26 8 * env DISPLAY=:0.0 /home/abid/.bin/task.sh > /home/abid/.bin/cronlog.txt
```


The command (script) is executed on time. This is confirmed by the presence of an /var/log/syslog entry as well as the correct message in the output.txt file as well as the Desktop notification. So the script is executed.

However the cronlog.txt file, although created, comes up empty (not the case if the same command is run via terminal). It is as if crontab simply skips over the 'cnee' command.

What am I doing wrong and how do I fix it?

---

### Post by llamabr on 2010-08-25
If task.sh is exiting without error, then:

/home/abid/.bin/task.sh

Should not have any output.  And so your cron.txt would be empty.  Or not empty, but what is placed there has no content.

You can check that it's being written to (even what's written is nothing) by checking the time stamp with:

```
ls -l /home/abid/.bin/cronlog.txt
```

---

### Post by abid_naqvi83 on 2010-08-25
By the nature of the command:

```
/home/abid/.bin/task.sh > cronlog.txt
```

the cronlog.txt file is created as soon as the script is called (or so I think). If the script works properly (for instance when this command is executed from a terminal) the cronlog.txt file contains the following output as a result of the cnee command being executed:

```
Close context** 163749896 163754512   context:83886081 ***
```

The fact that cronlog.txt comes up empty indicates that the cnee command was not executed properly. The recorded session was not played back at all. 

It is this problem that I need help resolving: Why the cnee command is not executed when called by crontab?

---

### Post by llamabr on 2010-08-26
The fact that cronlog.txt comes up empty indicates that the cnee command was not executed properly. The recorded session was not played back at all. 

Unless I misunderstand what you mean, in fact, the opposite is true.  The fact that it comes up empty indicates that the cnee command was executed properly.  the > symbol tells the script to send output to your cron.txt.  If it runs correctly, there's no output, and nothing is sent.

As you note, it runs successfully, so what do you expect to see as output?

---

### Post by abid_naqvi83 on 2010-08-26
When I run the script from the terminal the cronlog.txt file contains the following (as I have already said):

```
Close context** 163749896 163754512   context:83886081 ***
```

I take the appearance of this text as the indication of the correct running of the 'cnee' command. Even discounting it the cnee replay should have the mouse moving about clicking icons and buttons. None of this happens.

Furthermore the cnee replay session is 10 seconds long after which the Desktop Notification comes up. The script is not taking 10 seconds (doing nothing) but rather jumps straight to the notification. I have confirmed this by modifying the task.sh file as follows:

```
#!/bin/bash

# Launces an xnee Sessin file.

echo "Program Executed" > /home/abid/.bin/output.txt
date
cnee --replay -f /home/abid/.bin/task.xnr --time 2
date
notify-send "Debug" "Program Ends"
```

The output of the cronlog.txt file when called from crontab now reads:


```
Thu Aug 26 16:56:01 PKT 2010
Thu Aug 26 16:56:01 PKT 2010

```

As you can see the cnee command took no measurable time at all so clearly the 10 second long cnee recorded session was not played. The problem remains.

---

### Post by spjackson on 2010-08-26
> **abid_naqvi83 said:**
> 
```
# m h  dom mon dow   command
@hourly /home/abid/.bin/new_email.sh
44 4 26 8 * env DISPLAY=:0.0 /home/abid/.bin/task.sh > /home/abid/.bin/cronlog.txt
```The command (script) is executed on time. This is confirmed by the presence of an /var/log/syslog entry as well as the correct message in the output.txt file as well as the Desktop notification. So the script is executed.

However the cronlog.txt file, although created, comes up empty (not the case if the same command is run via terminal). It is as if crontab simply skips over the 'cnee' command.

I suggest redirecting error output to cronlog.txt too, i.e.
```

44 4 26 8 * env DISPLAY=:0.0 /home/abid/.bin/task.sh > /home/abid/.bin/cronlog.txt 2>&1
```and see if any errors are reported.

---

### Post by abid_naqvi83 on 2010-08-26
The issue has been resolved. I took spjackson's sage advice and edited the crontab entry to:

```
44 4 26 8 * env DISPLAY=:0.0 /home/abid/.bin/task.sh > /home/abid/.bin/cronlog.txt 2>&1

```

Upon execution by crontab the file cronlog.txt now contained the following:

```
Fri Aug 27 04:11:01 PKT 2010
/home/abid/.bin/task.sh: line 10: cnee: command not found
Fri Aug 27 04:11:01 PKT 2010

```

This suggested to me that whatever shell (if that is the correct word) was executing task.sh for crontab could not find the command cnee. So I performed a

```
$ locate cnee
```

and found the command at /usr/local/bin/cnee. I then explicitly called the cnee command with this path in task.sh as follows:

```
#!/bin/bash

# Launches an xnee session

/usr/local/bin/cnee --replay -f /home/abid/.bin/task.xnr --time 2
```

With this alteration the script works flawlessly when called by crontab. Thanks to everyone who participated.

---

