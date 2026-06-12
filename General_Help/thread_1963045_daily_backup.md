---
title: "daily backup"
date: 2012-04-21
forum: General Help
---

### Post by winzip on 2012-04-21
I  have a backup  script  **backup.sh**  in path  /home/user  which takes an input argument  to  run. 

Input argument is basically the date of backup I'm interested in.

Example: [B]./backup.sh   23-April-2012

[/B]After this script execution  this will create a directory **23-April-2012**  where all my data is backed up.



However ,as of  now , I am  running  this script manually.  I want to  run this script for daily backup and automate  the stuff at 11PM  daily.

Whats the easy workaround for this ?

---

### Post by Roasted on 2012-04-21
Set the script to be executable, and then add it to crontab with the name of the script under the "command" section. You can set it for every day at 11 PM (23:00).

---

### Post by Dave_L on 2012-04-21
Within a script, this will produce a string containing the current date in the format you're using:

$(date +%e-%B-%Y)

(Personally, I prefer a format like YYYY-MM-DD, to make sorting by date easier.)

---

### Post by raja.genupula on 2012-04-21
> **Roasted said:**
> Set the script to be executable, and then add it to crontab with the name of the script under the "command" section. You can set it for every day at 11 PM (23:00).

+1

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

use as reference .

---

### Post by winzip on 2012-04-22
> **raja.genupula said:**
> +1

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

use as reference .

Thanks I  have gone though the link . I was going through the manual and trying to understand how cron works . I  have a query at this part.


 reference  says cron command format is like this ...

**minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command **



why  you need to specify day  and weekday both ?week days are part of  day ..is not it ?  It seems redundant to me. please clarify this.

what  this would mean if  I  choose day =1 but  weekday=4  ?  this is a confusing selection .

---

### Post by winzip on 2012-04-22
> **Dave_L said:**
> Within a script, this will produce a string containing the current date in the format you're using:

$(date +%e-%B-%Y)

(Personally, I prefer a format like YYYY-MM-DD, to make sorting by date easier.)

I  have this snippet  presently ...

[I]mkdir  /home/user/$1/Data_bkp       [COLOR=Black]// $1  is the input argument .
[/COLOR][/I] 

Are you trying to say I  need to modify this way ?

*mkdir  /home/user/[COLOR=Blue]**$(date +%e-%B-%Y)**[/COLOR]/Data_bkp*

What  does *[COLOR=Blue]**%e-%B-%Y**[/COLOR]*  means ? I  dont understand these terms.

---

### Post by 1clue on 2012-04-22
You don't need to specify both.

Put a * in the one you don't care about, it matches all values.  

If you want it to hit every day at 3:21 AM then your entry would be this:

21 3 * * * /my/command

Also keep in mind that this script will NOT have access to your normal login environment.  You need to set all those variables manually.

Generally you don't supply input to these scripts.  You would want to calculate the date string inside the script.

---

### Post by winzip on 2012-04-22
> **1clue said:**
> You don't need to specify both.

Put a * in the one you don't care about, it matches all values.  



Thanks. But still  have a doubt when you specify  both.  just  to know -  its unclear yet.

> 
If you want it to hit every day at 3:21 AM then your entry would be this:

21 3 * * * /my/command

Do I need a [COLOR=Blue]**sudo**[/COLOR]  here ? I  dont login with **[COLOR=Blue]root[/COLOR] **.  But I can  work with [COLOR=Blue]**sudo **[/COLOR].

So I think format  should be like this ?

21 3 * * *   [COLOR=Blue]**sudo**[/COLOR]  /my/command

what do you say ?

> 
Also keep in mind that this script will NOT have access to your normal login environment.  You need to set all those variables manually.

Not  understood. I am worried here. Could you please elaborate /explain further ?

> 
Generally you don't supply input to these scripts.  You would want to calculate the date string inside the script.This is OK.

---

### Post by 1clue on 2012-04-22
The script runs only when ALL specified values match the current time.  If you specify both, then the time must match both values simultaneously.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)


Sudo:
If you need to run a script using cron with root authority, then install it into root crontab.  Running sudo from cron is not a good way to a happy linux box.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)


Environment:
Your environment, such as your PATH variable, does not exist for a service.  Your script does not run inside a login shell.  Cron scripts are considered to be system processes and as such everything needs to be explicitly defined.  It's a good idea to specify full path names for every command or script or file you reference from there.

It's not only possible but highly likely that a novice system admin or a novice user will thoroughly mess up their environment due to lack of understanding of how the system works.  Since cron will not only run the script once but continually at regular intervals, you really don't want a messed up environment to do something unexpected.

I seriously advise you to read [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) and practice with harmless scripts that run with your normal user authorization, not as root.

Another thing that won't exist with cron is terminal output.  You need to write your output appropriately so that you can find it, and so that it's managed correctly.

---

