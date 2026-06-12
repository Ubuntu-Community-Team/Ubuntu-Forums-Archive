---
title: "Bash script to sort oldest file in a directory"
date: 2012-08-04
forum: General Help
---

### Post by Stonecold1995 on 2012-08-04
I'm making a Bash script and I need it to be able to keep logs.  I want the log directory to contain at max 10 logs, and move all other logs to a sub-directory called "old".  This is the section of the script that is suppose to do that:

```
mkdir -p old

OLDEST=$(some_command)

if [ $(ls -l *.txt | wc -l) -gt 10 ]; then
   gzip -9 $OLDEST"
   mv *.txt.gz old"
fi

```

My problem is to find out how to get the oldest file.  So what do I have to put in "some_command" to get the name of the oldest file in the directory?  And by oldest file I mean the one with the oldest creation time.  This is the command I used to create the log file:

```
echo > $(date +%a_%b_%d_%T_%Z_%Y).txt
```

**So what do I have to substitute "some_command" with to get the desired result?**

---

### Post by papibe on 2012-08-04
Hi Stonecold1995.

Try this:
```
ls -1t | tail -1
```
Regards.

---

### Post by Stonecold1995 on 2012-08-04
> **papibe said:**
> Hi Stonecold1995.

Try this:
```
ls -1t | tail -1
```
Regards.

I did that but I'm still having some problems.  Here's what the script looks like:
```
LOGNAME="$(date).txt"
LOGDIR="logs"
MAX_LOGS=5
LOG="$LOGDIR/$LOGNAME.tmp.$$"

mkdir -p $LOGDIR

trap "echo \"Script recieved signal and will now terminate.\ > $LOG"
   rename 's/\'.tmp.$$'$//' $LOG
   cd $LOGDIR
   mkdir -p old
   if [ $(ls -l *.txt | wc -l) -gt $MAX_LOGS ]; then
      gzip -9 $(ls -1t *.txt | tail -1)
      mv *.gz old
   fi
   cd -
   exit $?" INT TERM

while true; do
   important_parts_of_the_script > $LOG
done
```

I keep getting errors when I run it.  When I tried running it in a directory with a bunch of sample logs, I got this:

```
alex@kubuntu:~/test$ ./test.sh
trap: usage: trap [-lp] [[arg] signal_spec ...]
Can't rename logs/Sat Aug  4 19:09:53 PDT 2012.txt.tmp.7562 logs/Sat Aug  4 19:09:53 PDT 2012.txt: No such file or directory
/home/alex/test
./test.sh: line 22: unexpected EOF while looking for matching `"'
./test.sh: line 24: syntax error: unexpected end of file
```

I'm guessing this has something to do with the parentheses.  Should I put them around every variable (like "$VAR" instead of $VAR)?  And if I do that but it is already within quotes (such as the quotes from the trap command), would I have to use / so it would be like "blah blah /"$VAR/" blah blah"?

What am I doing wrong here?

---

### Post by papibe on 2012-08-04
A few pointers:

trap is missing the signal type.

I can't tell exactly what is happening at the rename part, but I would recommend quoting all your variables.

Here, you are missing a quote:
```
exit $?" INT TERM 
```
Let us know how it goes.
Regards.

---

### Post by Stonecold1995 on 2012-08-04
I already had the quote there, and I thought I set INT and TERM as the signal times.

---

### Post by papibe on 2012-08-04
Here an example on how you can use trap:
```
#!/bin/bash

function graceful {
        echo
        echo "Stopping.."
        exit 0
}

trap graceful SIGHUP SIGINT SIGTERM

while [ 1 ]; do
        echo -n .
        sleep 1
done

```
Regards.

---

### Post by Stonecold1995 on 2012-08-04
Thank you very much, it works now!

What's the difference between SIGTERM and TERM, etc?

---

### Post by papibe on 2012-08-05
:D Great!

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

P.S.: Take a look at this [tutorial]("http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_12.html") about catching signals on bash.

---

### Post by sisco311 on 2012-08-05
The output of ls is formatted for humans and it will cause bugs in scripts. See:  [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Check out BashFAQ 003 (link in my signature).

I'd use logrotate to rotate the log files. ;)

---

