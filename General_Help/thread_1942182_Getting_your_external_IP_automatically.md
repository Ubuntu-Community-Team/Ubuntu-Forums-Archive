---
title: "Getting your external IP automatically"
date: 2012-03-17
forum: General Help
---

### Post by schrammbo on 2012-03-17
OK I am new to Linux (only dabbled in the past) and I had a problem, like so many do, with my external IP changing and not being able to access my system.

So I have created a couple of shell scripts that check the external IP address, Internal IP of the host and system name and then email to any location IF there is a change.  If there is no change it does nothing except place an entry in the syslog stating that the check took place.  

These are my very first attempts at shell scripts and they seemed to be working well so I thought I would pass them along.

I created one for use with a free client called SendEmail (google it) as I did not want a full email server on one system due to resource limitations and the other works with postfix.  T

They are pretty much identical scripts the main difference being the formatting of the mail so that the mail can be handled by the proper mail system.

I simply saved these as shell script files and then set them up to run via a cron job.

---

### Post by frenchn00b on 2012-03-17
```
  myextipaddress 
#!/bin/sh

if [ "$1" = "" ] ; then
        wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1

else

    echo `wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1`  > "$1"
    
    if [ "$2" = "date" ] ; then
        echo "The date is: $(date)" >> "$1"
    fi
    

fi

```

---

### Post by schrammbo on 2012-03-17
Ok Frenchnoob I have a question for you...

As I am not a programmer by trade and it took me several hours to make what I made can you be so kind as to translate this into english for me?

> **frenchn00b said:**
> ```
  myextipaddress 
#!/bin/sh

if [ "$1" = "" ] ; then
        wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1

else

    echo `wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1`  > "$1"
    
    if [ "$2" = "date" ] ; then
        echo "The date is: $(date)" >> "$1"
    fi
    

fi

```

I understand that the code is getting the external IP but how does the date come into play?

---

