---
title: "List users currently logged in?"
date: 2012-07-11
forum: General Help
---

### Post by irishetalon007 on 2012-07-11
I manage my family's computer remotely for them using ssh. Sometimes when performing upgrades and other tasks I need to reboot their computer for them, but before issuing the reboot command I'd like to see if any users are logged on, lest I kill an important task that someone is doing.

issuing "who" or "who -a" only lists my terminal log-ins. How can I see if any users are logged on?

(PS this is ubuntu 12.04, so it's using lightdm, if that means anything)

---

### Post by philinux on 2012-07-11
[http://www.thegeekstuff.com/2009/03/4-ways-to-identify-who-is-logged-in-on-your-linux-system/](http://www.thegeekstuff.com/2009/03/4-ways-to-identify-who-is-logged-in-on-your-linux-system/)

---

### Post by irishetalon007 on 2012-07-11
none of those work, all 4 of the suggestions from that link only show my username (the one i'm logged in to using ssh). 

(I know that someone else is logged in on the remote machine because I asked them to log in for this test)

---

### Post by erind on 2012-07-12
> **irishetalon007 said:**
> I manage my family's computer remotely for them using ssh. Sometimes when performing upgrades and other tasks I need to reboot their computer for them, but before issuing the reboot command I'd like to see if any users are logged on, lest I kill an important task that someone is doing.

issuing "who" or "who -a" only lists my terminal log-ins. How can I see if any users are logged on?

[...]

> 
none of those work, all 4 of the suggestions from that link only show my username (the one i'm logged in to using ssh). 

(I know that someone else is logged in on the remote machine because I asked them to log in for this test)     
Probably there is some other tool somewhere that can do that, but in the meantime you can filter the **ps** command to get something close to what you want.
The first code below will give you a list of users currently logged in, through GUI or (say) a ssh session,

```
ps axo user | egrep -v 'daemon|messagebus|syslog|USER|ntp|root' | sort -u

user3
user2
user1
```For a list of users that have a terminal assigned, say when logged in through a ssh session, try:

```
 ps axno user,tty | 
     awk  'BEGIN { print "USER  ID  TTY\n-------------" }
           NR==FNR { a[$3]=$1; next }
           $2!="?" && ($1 in a) && !/^[ \t]+0 tty[0-9]+$/ { 
                  if(!(($1,$2) in tty)) print a[$1], $1, $2 
                  tty[$1,$2]
             }
           ' FS=':' /etc/passwd  FS=' ' -


USER  ID  TTY
-------------
user2 1001 pts/0
user1 1000 pts/1
user1 1000 pts/2
user1 1000 pts/3
root  0   pts/3
user3 1002 pts/3


```

---

