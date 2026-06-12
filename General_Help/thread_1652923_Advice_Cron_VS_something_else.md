---
title: "Advice: Cron VS *something* else?"
date: 2010-12-25
forum: General Help
---

### Post by U2XS on 2010-12-25
I want to use my Linux box as a server to process images.  I already have the software in place & have created a Shell Script which works perfectly.  Now I need to set up the cron job.

Basically the shell script checks a folder for images.  If an image exists it process it accordingly & empties the folder.

I was going to set up a cron to run every minute.  Is this the best way to do it?  I am ok with waiting a minute or two, but I don't know if it's the most efficient way to do it.

---

### Post by efflandt on 2010-12-26
How long might the process take, worst case?  If it is still running while you run it again, is it going to fall all over itself?

I wrote this script to test if itself ( $0 ) is already running and exit if it is.  You could insert something like this at the beginning of your script, and once you are sure it is working, comment out the logging related lines (which may build up quickly running every minute):

```
#!/bin/bash
mylog=$HOME/only-one.log
/bin/date >> $mylog
# Check if already running
# count > 3 because ps and grep add 2 subprocesses
# what may look like single quotes are backticks (on ~ key of US keyboard)
if [[ `ps ax | grep -c $0` > 3 ]]; then
    echo already running >> $mylog
    exit 0
fi
echo running alone >> $mylog
# Do whatever we need to do
# sleep is just for testing
sleep 65
```If you use /bin/sh in shebang (1st) line instead of bash, the if then may need to be formatted differently (see **man dash**)

---

### Post by U2XS on 2010-12-26
That's a good question!  

My test run only ran for 20 seconds.  But considering the other variables (computer speed, other applications running & files to process), I can easily see it running for more than 1 minute.

So if I understand correctly, you *are* suggesting that I use a cron, however I should use that code as a failsafe so that it doesn't run two instances at once.

Thanks for the help!

---

