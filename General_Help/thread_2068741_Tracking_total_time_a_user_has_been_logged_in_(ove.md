---
title: "Tracking total time a user has been logged in (over a period of months)?"
date: 2012-10-09
forum: General Help
---

### Post by yanom on 2012-10-09
I need a way to track and display the amount of time a user has spent logged in to the system over the past day,week,month,year etc? I tried the acct package, but the AC command always just shows:
```
total   0.00
```

---

### Post by conradin on 2012-10-10
should we assume any given user is logging in, or out? 
I think you can use the last command to see who was logged in when. 
is this users on 1 computer or users on multiple computers like with LDAP?

---

### Post by conradin on 2012-10-10
I think you can use the last command to see who was logged in when. 
Im not sure where a con fig file is for last, but /var/log/wtmp is the file of logins.

the output of last on my system seems to be about 1 week

---

### Post by yanom on 2012-10-10
I want to track the **total time** a given user had been using the computer this month (day/week/year etc). It's only one machine, not a network.

---

### Post by yanom on 2012-10-11
.......buuuuuuuuuump.

---

### Post by raja.genupula on 2012-10-11
what i am thinking that , the past information you can't retrieve but you can make it available for future .

```
uptime
``` is BASH command   while gives the 

 
```
 19:56:23 up 32 min,  0 users,  load average: 0.53, 0.61, 0.66
``` 

there up will indicates the uptime . so what i suggest that  , you can have script like this and add to before shutdown .  
[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown#to-execute-a-script-at-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown#to-execute-a-script-at-shutdown)


```
raja@badfox:~$ cat try.sh 
#!/bin/bash

uptime >  uptime.txt
date
 awk '{print $3 $4}' uptime.txt
```

```
raja@badfox:~$ ./try.sh
Thu Oct 11 20:06:57 IST 2012
43 min
```

```
raja@badfox:~$ ./try.sh >> time.txt

```


so add this script to before shutdown so every time it will run automatically and stores the information  everytime with date also . so you can easily track his time history .

Thanks man , nice Question . 

PS : any improvements are welcome here .

---

### Post by yanom on 2012-10-11
> **raja.genupula said:**
> what i am thinking that , the past information you can't retrieve but you can make it available for future .

```
uptime
``` is BASH command   while gives the 

 
```
 19:56:23 up 32 min,  0 users,  load average: 0.53, 0.61, 0.66
``` 

there up will indicates the uptime . so what i suggest that  , you can have script like this and add to before shutdown .  
[http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown#to-execute-a-script-at-shutdown](http://en.kioskea.net/faq/3348-ubuntu-executing-a-script-at-startup-and-shutdown#to-execute-a-script-at-shutdown)


```
raja@badfox:~$ cat try.sh 
#!/bin/bash

uptime >  uptime.txt
date
 awk '{print $3 $4}' uptime.txt
```

```
raja@badfox:~$ ./try.sh
Thu Oct 11 20:06:57 IST 2012
43 min
```

```
raja@badfox:~$ ./try.sh >> time.txt

```


so add this script to before shutdown so every time it will run automatically and stores the information  everytime with date also . so you can easily track his time history .

Thanks man , nice Question . 

PS : any improvements are welcome here .

mmm, thanks for the reply. However, there are multiple accounts on this machine, and I need to see how long each account has used the machine for. Also, these sit in the community library, so much of the uptime will be spent at the login screen with nobody using it, but still accruing uptime.

---

### Post by raja.genupula on 2012-10-12
> **yanom said:**
> mmm, thanks for the reply. However, there are multiple accounts on this machine, and I need to see how long each account has used the machine for. Also, these sit in the community library, so much of the uptime will be spent at the login screen with nobody using it, but still accruing uptime.

ok check here . you can have the script running for logout 

[http://superuser.com/questions/127454/run-script-on-logout-shutdown-ubuntu](http://superuser.com/questions/127454/run-script-on-logout-shutdown-ubuntu)

---

