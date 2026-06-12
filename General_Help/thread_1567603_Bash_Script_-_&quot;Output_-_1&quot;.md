---
title: "Bash Script - &quot;Output - 1&quot;"
date: 2010-09-04
forum: General Help
---

### Post by zoller on 2010-09-04
Hi everyone,

I have a script that produces a small report of users that have successfully/unsuccessfully logged in and what users have used 'su' throughout the day via /var/log/auth.log

I will post some of the script to give you a better idea of what i'm attempting.

Variables (I think this is where my problems start)
```
cat=`cat /var/log/auth.log`
salog=`echo "$cat" | grep Accepted | awk '{ print "user " $9 " connected from ip address " $11 " at " $3 }'`

```

There are other logs that I am showing but they aren't needed for what I want to explain.

```
echo -n "Successful Logins:"; echo "$salog" | wc -l
```

The above is my issue. When this command is carried out, wc -l will return a value of 1 or higher. Even when there is nothing found in the log.

I am pretty sure that this is because of the variable $salog.
If I replace $salog with the actual content of the variable, wc -l will return 0 when the log is empty.

Does anyone know of a way to get around this?

Perhaps something like (i'm totally unsure about how to do this and this is a guess)

If $salog = less than or equal to 1
then - 1
fi

Then again, if I do this and there is 1 entry in the log, wc -l will still output 0..

Thanks for reading and I appreciate any advice you give.

---

### Post by DaithiF on 2010-09-04
Hi,
you could do:
```
[[ -z "$salog" ]] && count=0 || count=$(echo "$salog" | wc -l)
echo $count
```

also, i'm not sure why your reading the log file into a variable and then echoing that variable, why not just do:
grep Accepted /var/log/auth.log | awk ..etc

---

