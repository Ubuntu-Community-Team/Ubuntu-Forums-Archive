---
title: "run a bash script as a cron job"
date: 2012-05-12
forum: General Help
---

### Post by Scooter_X on 2012-05-12
Here's something in my crontab:


* * * * * home/riley/Scripts/updateWanIP.sh

and I can't for the life of me make out why it won't just run the dang script. The script itself works like a charm when run from terminal, but I can't figure why it won't run from the cron...

The basics of the script are:


#!/bin/bash

#This thing is supposed to log me in to my account and add to a file there.

rm ip


wget [http://mydomain.com/ip](http://mydomain.com/ip) 
echo "  It worked!!!!!!!!!!" >> ip 

scp ip [email]me@mydomain.com[/email]:~

---

### Post by codemaniac on 2012-05-12
> **Scooter_X said:**
> Here's something in my crontab:


* * * * * home/riley/Scripts/updateWanIP.sh

and I can't for the life of me make out why it won't just run the dang script. The script itself works like a charm when run from terminal, but I can't figure why it won't run from the cron...

The basics of the script are:


#!/bin/bash

#This thing is supposed to log me in to my account and add to a file there.

rm ip


wget [http://mydomain.com/ip](http://mydomain.com/ip) 
echo "  It worked!!!!!!!!!!" >> ip 

scp ip [email]me@mydomain.com[/email]:~
I guess in the cron entry you are missing the absolute path name of the script (a / is missing at the beginning) .

```
/home/riley/Scripts/updateWanIP.sh
```

---

### Post by Scooter_X on 2012-05-12
Found it. Simple. 

* * * * * sh /home/riley/Scripts/updateWanIP.sh

So I probably did need the / in front of home but when it came down to it, 'sh' is what I needed. I figured #!/bin/bash would've done the same but didn't. Maybe I should've tried just /bin/bash...

---

### Post by papibe on 2012-05-12
Hi Scooter_X.

I would also add full path to all references to your 'ip' file.

For instance:
```
rm  /path/to/ip
...

echo "It worked!!!!!!!!!!"  >>   /path/to/ip
```
Regards.

---

