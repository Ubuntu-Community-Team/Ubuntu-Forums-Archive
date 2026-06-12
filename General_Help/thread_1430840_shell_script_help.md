---
title: "shell script help"
date: 2010-03-15
forum: General Help
---

### Post by ryanf4321 on 2010-03-15
I was wondering if someone could help me finish this script. It is to see who is active on the host (active is idle time being less than 1 minute. It's using the s for seconds as being "active")


for people in `w -h | cut -b 49`
do
        if [ $people = s ]

        then

                echo $y is currently active
        fi
done

For the life of me, I can't figure out how to make it echo the users name along with the cut information from above. Right now it just prints 

"is currently active" for each user. I want it to print their      username too, like "Jim is currently active", "bob is currently active", etc. Anyone know how this would be possible? thanks.

---

### Post by sandyd on 2010-03-15
> **ryanf4321 said:**
> I was wondering if someone could help me finish this script. It is to see who is active on the host (active is idle time being less than 1 minute. It's using the s for seconds as being "active")


for people in `w -h | cut -b 49`
do
        if [ $people = s ]

        then

                echo $y is currently active
        fi
done

For the life of me, I can't figure out how to make it echo the users name along with the cut information from above. Right now it just prints 

"is currently active" for each user. I want it to print their      username too, like "Jim is currently active", "bob is currently active", etc. Anyone know how this would be possible? thanks.
```

man awk
```
```

man grep
```
```

who | grep pts | awk -F "pts" '{print $1}'

```

---

### Post by prodigy_ on 2010-03-15
Try this:

```

#!/bin/sh
IFS=$(printf "\n\b")
USERS=$(w -h)
for I in $USERS
do
  IDLE=$(printf "%s" "$I"|awk '{ print $5 }'|grep "s")
  if    [ "$IDLE" != "" ]
    then
        ACTIVE=$(printf "%s" "$I"|awk '{ printf $1 }')
        printf "%s\n" "User $ACTIVE is active"
  fi
done

```

---

### Post by ryanf4321 on 2010-03-15
prodigy,

this seems to do the trick. thanks alot!

---

### Post by asmoore82 on 2010-03-15
> **prodigy_ said:**
> Try this:

```

#!/bin/sh
IFS=$(printf "\n\b")
USERS=$(w -h)
for I in $USERS
do
  IDLE=$(printf "%s" "$I"|awk '{ print $5 }'|grep "s")
  if    [ "$IDLE" != "" ]
    then
        ACTIVE=$(printf "%s" "$I"|awk '{ printf $1 }')
        printf "%s\n" "User $ACTIVE is active"
  fi
done

```
!! This will find a user that has been idle for days as active...

the 's' in "2days" is in the exact same position as in "0.00s"

---

### Post by prodigy_ on 2010-03-15
> **asmoore82 said:**
> This will find a user that has been idle for days as active...
I said "try", because it was an example to give some idea of what needs to be done. I didn't explore all the possibilities. Still, if you insist: 
```
#!/bin/sh
IFS=$(printf "\n\b")
USERS=$(w -sh)
for I in $USERS
do
  IDLE=$(printf "%s" "$I"|awk '{ print $4 }'|sed -e '/.*[0-9]s/d')
  if    [ "x$IDLE" = "x" ]
    then
        ACTIVE=$(printf "%s" "$I"|awk '{ print $1 }')
        printf "%s\n" "User $ACTIVE is active"
  fi
done

```

---

### Post by asmoore82 on 2010-03-16
> **prodigy_ said:**
> I said "try", because it was an example to give some idea of what needs to be done. I didn't explore all the possibilities. Still, if you insist: 
```
#!/bin/sh
IFS=$(printf "\n\b")
USERS=$(w -sh)
for I in $USERS
do
  IDLE=$(printf "%s" "$I"|awk '{ print $4 }'|sed -e '/.*[0-9]s/d')
  if    [ "x$IDLE" = "x" ]
    then
        ACTIVE=$(printf "%s" "$I"|awk '{ printf $1 }')
        printf "%s\n" "User $ACTIVE is active"
  fi
done

```

:razz: What's with all the printf's?
you must have a strong background in C/C++

Anytime you have to manipulate the IFS, it's a good
indication that there must be a simpler solution.
'while read' almost always works in these situations:
```
#parse multi-line input the easy way
w -sh | while read line
do
#trivial 'while' example; let's eat whitespace
   eval echo "$line"
done
```

I'm not entirely certain that your RegEx '.*[0-9]s' matches
exactly what you think it does, test it out:
```
w -sh | egrep --color=force '.*[0-9]s'
```
I believe we would be better off to just filter out what we want up front.

Eureka! a one-liner:
```
w -sh | awk '{ print $1 " " $4 }' | egrep ' [.0-9]{4,5}s$' | awk '{ print $1 " appears to be Active." }' | sort | uniq
```

---

### Post by prodigy_ on 2010-03-16
> **asmoore82 said:**
> :razz: What's with all the printf's?
you must have a strong background in C/C++
No, but I like printf because it always works.

> **asmoore82 said:**
> I'm not entirely certain that your RegEx '.*[0-9]s' matches
exactly what you think it does
Thanks, I'm entirely certain it matches what I think it does.

---

