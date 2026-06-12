---
title: "logrotate"
date: 2010-02-22
forum: General Help
---

### Post by i_berbeu on 2010-02-22
Hello,
i have been looking for the answer for a long time but i didn't found anything.
when i use logrotate like this

logrotate -t process -f /var/log/tempfile "message"

If the file /var/log/tempfile doesn't exists it doesn't do anything, which i think is normal, but if i create that file using

touch /var/log/tempfile

and then i type logrotate -t.......... all seems to be ok but when i go to see the content of that file, it is empty, and the "message" message is in the file /var/log/messages

Could anyone help me please?

---

### Post by gmargo on 2010-02-22
As far as I know, **logrotate** never writes to the log files (it's own status is sent to the syslog daemon which puts it in the default messages file).  Also, there's no -t option.  And no "message" field.

Perhaps you are thinking of the **logger** command.

```

$ logrotate --help
Usage: logrotate [OPTION...] <configfile>
  -d, --debug               Don't do anything, just test (implies -v)
  -f, --force               Force file rotation
  -m, --mail=command        Command to send mail (instead of `/usr/bin/mail')
  -s, --state=statefile     Path of state file
  -v, --verbose             Display messages during rotation

$ logger --help
logger: invalid option -- '-'
usage: logger [-is] [-f file] [-p pri] [-t tag] [-u socket] [ message ... ]

```

---

### Post by i_berbeu on 2010-02-22
sorry,
i was wrong. what i wanted to say is logger. So, change the word logrotate by logger in my first post.
This confusion is because i have another question about logrotate.....
When i type
logrotate /var/log/tempfile
a file called tempfile.1 is created (under the conditions described in the corresponding .conf file), but logs still writing in that new tempfile.1 unless i restart the process which write on it.
So.... Is neccesary then, to restart the service to do logrotate do a good work???

I can't find enough information to solve my problem
Thanks!

---

### Post by gmargo on 2010-02-22
The **logrotate** configuration files take care of restarting the process.  Look at some of the files in **/etc/logrotate.d/** (and of course the man page).  For daemons, the config file generally has a **postrotate** field that takes care of telling the service to reload/restart.

---

### Post by i_berbeu on 2010-02-23
thanks for your answer, it solves my doubts.

And what about my problem with looger, does anybody know what i must do??

---

### Post by gmargo on 2010-02-23
**logger** sends a message to the syslog daemon.  The message comes from either the command line, or if not specified then the file given with the -f option, or if not specified then standard input.  The -f option does not specify the destination of the message.  That is controlled by the syslog daemon's configuration file.

---

