---
title: "Bash scripting"
date: 2010-02-10
forum: General Help
---

### Post by thomashw on 2010-02-10
I want to use "sleep" in a bash script to count down to a certain hour each day.

What I need is to find the time NOW, find the difference between NOW and 2am, and sleep for that many seconds.

So, using bash, how can I find the time NOW and find the difference to 2am?

---

### Post by Satoru-san on 2010-02-10
sounds like you rather need to learn2crontab

```
man crontab
```

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference) <-- that is helpful too.

---

### Post by thomashw on 2010-02-10
If the command I run with cron requires input from the user (me), will it prompt me?

Reason being, the thing I am running at 2am usually needs input from me at some point, which is why I run it in the terminal.

---

### Post by Satoru-san on 2010-02-10
> **thomashw said:**
> If the command I run with cron requires input from the user (me), will it prompt me?

Reason being, the thing I am running at 2am usually needs input from me at some point, which is why I run it in the terminal.
o_O

what could you possibly need to be up at 2am to do on your computer that you cant just do at 6am or 9pm

Also what script are you running that needs user input?
If its like a password you can add the cron as root and you wont need to enter a password.

---

### Post by t4thfavor on 2010-02-10
Can you use cron, with zenity for basic user input? I believe that would make it happen, also if you cron it, there will be no problem if the machine accidentally gets rebooted or something.

+1 on what script, as if we see what you are doing, perhaps it can be automated to run without user intervention.

---

### Post by thomashw on 2010-02-10
I'm not up at 2am. I'm syncing files. It's a lot of files, so it takes a long time to scan. Once they're scanned, if there is anything not making sense, the user (me) needs to decide which way to propagate the sync.

So, I start the sync at 2am. And, if need be, it's ready for me by the time I get up in the morning. If it doesn't need any input from me, then it syncs by itself.

So, I figure it'd be easier to run this from a terminal. If a cron job will prompt me, that will work as well, but I haven't read any indication that it would.

---

### Post by t4thfavor on 2010-02-11
Something like this I guess will do the trick.

```

#!/bin/bash
now=`date "+%H:%M"`;
target=02:00;
while [ "$now" !=  "$target" ]; do
    now=`date "+%H:%M"`;
    echo "it is not ${target} o clock yet. It's only `date "+%H:%M:%S"` ";
    sleep 10;
done
#Do your stuff


```


Also have a look at this, if the above is not suitable.
[http://www.unix.com/tips-tutorials/31944-simple-date-time-calulation-bash.html](http://www.unix.com/tips-tutorials/31944-simple-date-time-calulation-bash.html)

---

### Post by thomashw on 2010-02-11
Thank you for the link and your code!

Here's what I came up with for myself:

```

#!/bin/bash

date2stamp () {
    date --utc --date "$1" +%s
}

stamp2date (){
    date --utc --date "1970-01-01 $1 sec" "+%Y-%m-%d %T"
}

dateDiff (){
    case $1 in
        -s)   sec=1;      shift;;
        -m)   sec=60;     shift;;
        -h)   sec=3600;   shift;;
        -d)   sec=86400;  shift;;
        *)    sec=86400;;
    esac
    dte1=$(date2stamp $1)
    dte2=$(date2stamp $2)
    diffSec=$((dte2-dte1))
    if ((diffSec < 0)); then abs=-1; else abs=1; fi
    temp=$((diffSec/sec*abs))
}

while( true )
do
target=04:00:00
now=`date "+%H:%M:%S"`;

echo "Will begin syncing with server at $target."
dateDiff -h "$now" "$target"
hours=$((24-$temp))
dateDiff -m "$now" "$target"
mins=$((1440-$temp))
echo "$hours hours (or $mins minutes) to wait as of $now."

dateDiff -s "$now" "$target"
wait=$((86400-$temp))
sleep $wait

# Add code here for whatever you want to do at 4am each morning.
# I'm using a program to sync my files between computers/a remote server.

done

```

---

### Post by john newbuntu on 2010-02-11
My approach to do this would be to set up a cron at a certain time for the virus scan and if successful follow up with rsync or any other sync utility on the successful files.  Write the unsuccessful files to a directory.  Any errors encountered will be mailed to the root.  Just check your mail in the morning and continue from where you left off. Or throw an icon on your desktop that says something failed.

---

### Post by rnerwein on 2010-02-11
> **t4thfavor said:**
> Can you use cron, with zenity for basic user input? I believe that would make it happen, also if you cron it, there will be no problem if the machine accidentally gets rebooted or something.

+1 on what script, as if we see what you are doing, perhaps it can be automated to run without user intervention.

hi
yes you can use zenity - but with some restrictions i think.
your desktop must be up ( i think you must be loged in ) and you have to figure out the value of your DISPLAY seting: env | grep DISPLAY
here is a little example - using a script in my ~/scripts/zenity.sh
#!/bin/sh
xhost +localhost
DISPLAY=:X.0        # X you have to figure out
export DISPLAY
/usr/bin/zenity  --question --title='=> message for XYZ <=' --text='time to have a break'
echo "returned: $?" >/home/XYZ/tmp/zenity.txt
exit 0
                                                  ;)

---

