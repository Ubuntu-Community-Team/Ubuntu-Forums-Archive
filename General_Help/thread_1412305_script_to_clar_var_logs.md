---
title: "script to clar var logs"
date: 2010-02-21
forum: General Help
---

### Post by ibizatunes on 2010-02-21
Hello, im tring to setup a script that will clear /var/log/ when the partition reaches 75% full, and deletes anything that is over 30days old, i have this so far, im a NEWBIE when it comes to scripting, 

```
df -h | grep /var/logs/ | awk '{ print $5 }' | $DISK_UTIL
if [ $DISK_UTIL => 75% ]
find /var/logs/ -type f -mtime +30 -exec rm -- {} \; 
exit
fi
```

i know im 'grepping' for the number correctly but i'm not assigning that number to the variables $DISK_UTIL

Any help would be great

---

### Post by lloyd_b on 2010-02-21
> **ibizatunes said:**
> Hello, im tring to setup a script that will clear /var/log/ when the partition reaches 75% full, and deletes anything that is over 30days old, i have this so far, im a NEWBIE when it comes to scripting, 

```
df -h | grep /var/logs/ | awk '{ print $5 }' | $DISK_UTIL
if [ $DISK_UTIL => 75% ]
find /var/logs/ -type f -mtime +30 -exec rm -- {} \; 
exit
fi
```

i know im 'grepping' for the number correctly but i'm not assigning that number to the variables $DISK_UTIL

Any help would be great

Try ```
DISK_UTIL=`df -h | grep /var/logs/ | awk '{ print $5 }'`
```The backticks (above the tab key on US keyboards) tells it to run the command and return the output, which is then assigned to DISK_UTIL.

Lloyd B.

---

### Post by ibizatunes on 2010-02-21
Thanks very much lloyd_b, your a star!

---

### Post by ibizatunes on 2010-02-21
just have thought about it more my log file in var/logs fills up quickly would this code work
```

#!/bin/sh
DISK_UTIL=`df -h | grep /var/logs/ | awk '{ print $5 }'`
# The %
if [ $DISK_UTIL => 95% ]; then
find /var/logs/ -type f -mtime +5 -exec rm -- {} \; 
elif [ $DISK_UTIL => 90% ]; then
find /var/logs/ -type f -mtime +10 -exec rm -- {} \; 
fi
		if [ $DISK_UTIL => 85% ]; then
		find /var/logs/ -type f -mtime +15 -exec rm -- {} \; 
		elif [ $DISK_UTIL => 80% ]; then
		find /var/logs/ -type f -mtime +20 -exec rm -- {} \; 
		fi
if [ $DISK_UTIL => 75% ]; then
find /var/logs/ -type f -mtime +30 -exec rm -- {} \; 
fi
exit

```

---

### Post by lloyd_b on 2010-02-22
> **ibizatunes said:**
> just have thought about it more my log file in var/logs fills up quickly would this code work
```

#!/bin/sh
DISK_UTIL=`df -h | grep /var/logs/ | awk '{ print $5 }'`
# The %
if [ $DISK_UTIL => 95% ]; then
find /var/logs/ -type f -mtime +5 -exec rm -- {} \; 
elif [ $DISK_UTIL => 90% ]; then
find /var/logs/ -type f -mtime +10 -exec rm -- {} \; 
fi
		if [ $DISK_UTIL => 85% ]; then
		find /var/logs/ -type f -mtime +15 -exec rm -- {} \; 
		elif [ $DISK_UTIL => 80% ]; then
		find /var/logs/ -type f -mtime +20 -exec rm -- {} \; 
		fi
if [ $DISK_UTIL => 75% ]; then
find /var/logs/ -type f -mtime +30 -exec rm -- {} \; 
fi
exit

```

Sorry about this, but I wasn't really looking at most of the code on your initial question, so I missed a few other problems with it.  All I worried about was answering "how do I get the result of a command into a shell variable"...

1.  "=>" is not a valid comparison in the shell language (at least for bash).  There is a real issue with using "<" or ">" at all, as these are used by the shell for redirecting output.  As such, the shell provides alternatives for all comparisons:```

  -eq "Equal to"
  -ne "Not equal to"
  -lt "Less than"
  -le "Less than or equal to
  -gt "Greater than"
  -ge "Greater than or equal to"
```

2.  The "grep" is redundant - "awk" is quite capable of handling this part as well as limiting which field to print.

3.  "85%" is a *string*, not a numeric value.  As such it needs to be in quotation marks.  There is also an oddball issue to worry about - with string comparisons, "100%" is actually less than "99%" (any string beginning with "1" will evaluate to less than a string beginning with "9").  I would suggest you "trim" that percent sign off, and then you can use strictly numeric comparisons, avoiding that 100% issue.  This can also be accomplished by the "awk" command ("awk" is a sort of "swiss army knife" that can replace a bunch of different standard commands).

4.  Your code assumes that "/var/log" is a filesystem in its own right.  That may be true, but that is NOT how many systems are configured (where "/var/log" is part of either the root filesystem or the "/var" filesystem if there is one).  I'd suggest specifying "/var/log" to the "df" command - this will return the info only for the filesystem "/var/log" lives on, regardless of the mount point, so you only have to search for "/dev" to skip the header line.

Now for something new - you're using multiple "if" statements, when you should be using only one.  An "if" can support any number of "elif" clauses, with only the first one that evaluates to TRUE being executed.

Here's a rewrite of you code, fixing all of the problems listed:```
#!/bin/sh

# Use "df" to get the free percentage for whatever filesystem "/var/log" is on
# A note on the awk - slashes in the search string need to be "escaped" with
# backslashes, since awk uses slashes to define the "search" string.
# Adding 0 to a field is a cheap way of stripping the percent sign...
DISK_UTIL=`df -h /var/log | awk ' /\/dev/ { print ($5 + 0) }'`

# Now test against various conditions, from highest to lowest
if [ $DISK_UTIL -ge 95 ]; then
    find /var/logs/ -type f -mtime +5 -exec rm -- {} \; 
elif [ $DISK_UTIL -ge 90 ]; then
    find /var/logs/ -type f -mtime +10 -exec rm -- {} \; 
elif [ $DISK_UTIL -ge 85 ]; then
    find /var/logs/ -type f -mtime +15 -exec rm -- {} \; 
elif [ $DISK_UTIL -ge 80 ]; then
    find /var/logs/ -type f -mtime +20 -exec rm -- {} \; 
elif [ $DISK_UTIL -ge 75 ]; then
    find /var/logs/ -type f -mtime +30 -exec rm -- {} \; 
fi
exit
```Now for the usual disclaimer - I have *not* actually tested this code.  For one thing, I don't even *have* a "/var/log" filesystem :)

I'd suggest replacing the various "find" commands with simple "echo" statements, and then test it that way.  Sorry for the long response, but I wanted to do it right this time. :)

Lloyd B.

---

