---
title: "logging with logger"
date: 2009-12-28
forum: General Help
---

### Post by Baruch on 2009-12-28
Hi.
I have a server using Dynamic DNS for two domains. My dyndns server provided a URL to update the DNS record. Each time the URL is fetched, it updates the record and returns the word 'success' for each domain, like this:
success
success
I have a script to fetch the URL with wget which runs every 15 minutes with cron. At the moment it works like this: the script fetches the URL into a temporary file. It then logs the file contents to the syslog with
```
logger -t ddupdt -f $tempfile
```
The problem is that I only see one of the success lines in the syslog until something else is logged. Once something else appears in the syslog, both my lines appear with the correct time (= the second one doesn't get the time it finally appeared).
My guess is that I have to flush the logger somehow, but how?:confused:

Another thing. Ideally I would like both of those lines to be compacted into one and logged to a separate log file, say /var/log/dyndns. How would I go about either of these? (My scripting abilities are pretty limited, so if someone could post an example script for combining the lines into one it would be helpfull)

Thanks alot.

---

### Post by Barriehie on 2009-12-28
Post the script you're using and the contents of the file it's generating please! :)

Barrie

Edit: In regards to your own log file see if [my post here](http://ubuntuforums.org/showthread.php?t=1342548) will do what you're looking for.

---

### Post by Baruch on 2009-12-29
> **Barriehie said:**
> Post the script you're using and the contents of the file it's generating please! :)

Barrie

Edit: In regards to your own log file see if [my post here](http://ubuntuforums.org/showthread.php?t=1342548) will do what you're looking for.

Here is the script:
```
#!/bin/bash

t=$(tempfile)
wget -O $t "https://www.sitelutions.com/dnsup?[...]"
logger -t ddupdt -f $t

```
And here is the temporary file:
```
success
success

```

That link wasn't what I was looking for. I am not even using a GUI. I am looking for a way, either with logger, another built-in command, or a script, to build a file that has the same structure as the standard log files, so that I can use the same tools on it, whether it is script that processes it or the GNOME log file viewer, or any other log file tool.

EDIT: Should I add "rm $t" at the end of the script?

---

### Post by Barriehie on 2009-12-29
Still have some work to do but this is getting closer.  I don't run a full blown server but browsing through synaptic showed me log2mail.  From the description it looks like it can email you based on regexpr matching, i.e. you can get an email when NOT success(ful).  Until I can do some more digging or another poster chimes in I'm sure there's a utility to look at custom logfiles.

This script is written to wait 15 minutes between cycles so you don't have to keep 'cron'ning the job.  That just makes more logfile entries!  As it stands now this script improves on your current situation by generating less cron logfile entries and should flush the buffers after each cycle.  It also generates a PID file.

```

#!/bin/bash

# PID File
echo $$ > /var/run/MyLogFile.pid

LOOPER="TRUE"
t=$(/PathToLogFile/LogFile)
stopfile="PathToStopFile/stopfile"

if [ -e /PathToLogfile/LogFile ]; then
  rm /PathToLogfile/LogFile
else
  touch /PathToLogfile/LogFile
fi

while [ "$LOOPER" = "TRUE" ]
do

#
# Test domain 1 - write to LogFile
#
    wget -o $t "https://www.sitelutions.com/dnsup?[...]"
#
# Test domain 2 - Append to LogFile
#
    wget -a $t "https://www.sitelutions.com/dnsup?[...]"

#
# Missing code to generate 1 line, gawk can do this!
#

#
# Write to system log
#
    logger -t ddupdt -f $t
#
# Flush the logger output
#
    logger -f $t " "

#
# Nuke the logfile
#
  rm /PathToLogfile/LogFile

    sleep 900                   # Wait 15 minutes

    if [ -e $STOPFILE ]         # Keep running or stop?
    then
        rm $STOPFILE
        rm /var/run/MyLogFile.pid
        exit 1
    fi
done

```

Barrie

Edit: Wouldn't take to much to make this launch at boot time like a daemon. Once the gawk part is completed.

---

### Post by Barriehie on 2009-12-29
Okay, since I'm trying to learn gawk this was a good excercise!  We've got *oldlogfile* containing ```
success
success
``` 1st line is domain 1 and 2nd line is domain 2, I'm assuming.

and a *gawkfile.gawk* containing: ```

#!/usr/bin/gawk
##
## gawkfile.gawk
## 
## Made by Barrie
## Login   <barrie@localhost>
## 
## Started on  Tue Dec 29 16:50:14 2009 Barrie
##
{
    for( i=1; i<=2; i++ )
        datum[i]=$0
}

END {
    print "Domain 1 " datum[1] " - Domain 2 " datum[2]
}

```

When we run:
```

gawk -f gawkfile.gawk ./oldlogfile > ./newlogfile

```
we get *newlogfile* looking like:
```

Domain 1 success - Domain 2 success
```

Don't know how yet but I'm sure we can put date/time stamps in there somewhere. ( still working on the custom logfile location/name thing)

Barrie

Edit: Still reading up on conditionals which implies that if either domain1 or domain2 is != "success" then we can generate an oops file somewhere, which a daemon can pick up and generate an email.  Do you have postfix or something similar installed? - not to digress but I can think faster than I can type! :)

---

### Post by Baruch on 2009-12-30
My server is inaccessibale at the moment (it's at a freinds house, so I can't even check why), but I tried this yesterday
```
$t=`wget -O - "http://..."`
logger -t ddupdt -pri user.info -- $t
```
and for some reason it worked (that is, both lines are now on one, like so:)
```
success success
```
I would like to understand what/why your scripts, but the talk was a little over my head.
What is gawk?
How to make it run like a deamon? Why would I want to do that? Wouldn't it just use more resources if it was constantly running?
Why have a special file whose sole purpose is to stop the execution of the script? Couldn't it just be stopped manually instead of creating a new file and waiting 15 minutes? Is this a common practice in professional Linux scripts?
And what is a PID file? What is it's purpose? What is /var/run anyway?

---

### Post by Barriehie on 2009-12-30
> **Baruch said:**
> My server is inaccessibale at the moment (it's at a freinds house, so I can't even check why), but I tried this yesterday
```
$t=`wget -O - "http://..."`
logger -t ddupdt -pri user.info -- $t
```
and for some reason it worked (that is, both lines are now on one, like so:)
```
success success
```
Good!

> **Baruch said:**
> I would like to understand what/why your scripts, but the talk was a little over my head.
What is gawk?Gawk is the GNU version of AWK, a popular, powerful stream editor.  It's pretty cool!  For instance, I'm running squid on here as a web filter and once a week cron runs a script that downloads the new blacklist.  I take the output of the tar extraction and it gets piped to a file.  BASH builds the first part of a new script and gawk then runs through the tar output file and builds the rest of the script for concatenating the different urls and domains.  When gawk is done control is passed back to BASH and my squid installation is updated with the new list; i.e. merged with the previous data.  At certain points in the process results are echoed to a log file which has been added to the key value of gnome-system-log so it can be viewed with the other logs.  Gawk is a very cool tool!  You can find out about gawk/awk [here](http://awk.info/).
> **Baruch said:**
> How to make it run like a deamon? Why would I want to do that? Wouldn't it just use more resources if it was constantly running?To daemonize a script you put it in /etc/init.d and then use update-rc.d to update the various runlevels.  Take a look in /etc/init.d and you'll see what can get started.  I was thinking in terms of logfiles, daemonizing it would eliminate the entries being made in your cron log.  A particular daemon I've got running on here uses about 1.5 megs of RAM and when it wakes up I've never noticed.  
> **Baruch said:**
> Why have a special file whose sole purpose is to stop the execution of the script? Couldn't it just be stopped manually instead of creating a new file and waiting 15 minutes?You could do it either way and there are ways to kill is instantly.  I use a stop file via an alias so I don't have to go through the sudo command.  I type 'stp' in the cli and it's done.> **Baruch said:**
>  Is this a common practice in professional Linux scripts?Don't know! easier for me with a stop file and an alias!
> **Baruch said:**
> And what is a PID file? What is it's purpose? What is /var/run anyway?PID = Process ID.  The PID file is/can be used by other resources to determine if a process is running.  The directory /var/run is where the PID files are kept.

Barrie

Edit: Well, except for having a custom log file it appears that you've got it.  You could still pipe to a custom file and use tail or some such.  I'm not familiar with whatever you're using to view your logfiles.  I'm running a desktop setup and use my server for pic hosting, web language learning and NOT having to pay someone for it. :)

---

### Post by Baruch on 2009-12-31
Thanks for the help. I'm not using any specific logfile viewer. I just wanted to have the same format so that any tool that could work with the standerd log coould work with the custom one. It's not really too importent. I can live with it n /var/log/messages

---

### Post by Barriehie on 2009-12-31
You might want to take a look at /etc/syslog.conf  That's the configuration file for the syslogd utility and I think if you put your file in there it will be included with the logrotate files.

Barrie

Edit: man -k syslog turns up the following list which may be of use.

```

/usr/sbin/lm-syslog-setup (8) [lm-syslog-setup] - configure laptop mode to sw...
lm-syslog-setup (8)  - configure laptop mode to switch syslog.conf based on p...
logger (1)           - a shell command interface to the syslog(3) system log ...
Sys::Syslog (3perl)  - Perl interface to the UNIX syslog(3) calls
syslog-facility (8)  - Setup and remove LOCALx facility for sysklogd
syslog.conf (5)      - syslogd(8) configuration file
syslogd (8)          - Linux system logging utilities.
syslogd-listfiles (8) - list system logfiles
```

---

