---
title: "Run Script at Boot / Login screen"
date: 2010-09-12
forum: General Help
---

### Post by ductiletoaster on 2010-09-12
ok i have made this script to do an automated remote rsync of my windows machine. 

I have my router set to wake my server up every monday at 10:00am

I want to then have this script run when the computer hits the login screen.... However I only want it to run on that specific day.

how would i have it do this. It needs to just rsync to my users home directory.

My thoughts: have the script check the day and if it is the right day it executes. The script does an automated login of my user?

I need help!

---

### Post by Lukas666 on 2010-09-12
> **ductiletoaster said:**
> ok i have made this script to do an automated remote rsync of my windows machine. 

I have my router set to wake my server up every monday at 10:00am

I want to then have this script run when the computer hits the login screen.... However I only want it to run on that specific day.

how would i have it do this. It needs to just rsync to my users home directory.

My thoughts: have the script check the day and if it is the right day it executes. The script does an automated login of my user?

I need help!

How long do you expect this process to take? Is it a good idea to start it at log on?

If so, have a look here: [http://www.weberdev.com/get_example-4194.html](http://www.weberdev.com/get_example-4194.html)

---

### Post by ductiletoaster on 2010-09-12
> **Lukas666 said:**
> How long do you expect this process to take? Is it a good idea to start it at log on?

If so, have a look here: [http://www.weberdev.com/get_example-4194.html](http://www.weberdev.com/get_example-4194.html)

Well I actually need it to either happen bfore log on or to have the script automatically login as a specific user then execute

---

### Post by wojox on 2010-09-12
Take a look [at]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=a/at") and/or [crond]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/crond")

---

### Post by ductiletoaster on 2010-09-12
on of the issues is that my script has som sudo commands in it.... and I cant figure out how to get them to run without having to manually type in the password

Ok well cron jobs was just not what i needed so i added this little part to the script that checks the day and the hour and compares it.
so basically if the script runs any time on Monday between 10:00-10:59am then it will complete the script

Anyother time it will exit

---

