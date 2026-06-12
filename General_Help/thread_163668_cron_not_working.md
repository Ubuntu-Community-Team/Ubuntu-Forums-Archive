---
title: "cron not working"
date: 2006-04-21
forum: General Help
---

### Post by yyagol on 2006-04-21
Hi
i am trying to crontab a script but it didnt work so
i desided to check on cron and it came out that
cron was mot working at all . thi is what i did :
```
yyagol@Bitch:~$ crontab -l
# m h  dom mon dow   command
*/1 * * * * echo "pipipipipipippip"
yyagol@Bitch:~$ pgrep -l cron
5943 cron
yyagol@Bitch:~$ date
&#1493;' &#1488;&#1508;&#1512; 21 17:31:39 IDT 2006
yyagol@Bitch:~$ date
&#1493;' &#1488;&#1508;&#1512; 21 17:33:05 IDT 2006
yyagol@Bitch:~$ sudo /etc/init.d/cron restart
 * Restarting periodic command scheduler...                                          [ ok ]
yyagol@Bitch:~$ date
&#1493;' &#1488;&#1508;&#1512; 21 17:33:25 IDT 2006
yyagol@Bitch:~$ date
&#1493;' &#1488;&#1508;&#1512; 21 17:36:04 IDT 2006
yyagol@Bitch:~$ pgrep -l cron
5973 cron
yyagol@Bitch:~$

```
i even try to reinstall cron but it did not help
so cron is running but it would not schedule
and ther are no errors at all. i try to run cron at text mode.
any idea ???

---

### Post by cgjones on 2006-04-21
Try replacing the */1 with * to see if it will work.

---

### Post by yyagol on 2006-04-21
I did that too i also did 0-59 * * * *
still nothing

---

### Post by cgjones on 2006-04-21
Is the script you are trying to run doing anything that it would need root privileges for?

---

### Post by yyagol on 2006-04-21
well it dose but i edit crontab -e wile login as root and when nothing happend
i start wondering why .
as you can see i just try cron to do a simple task **echo**.
```
yyagol@Bitch:~$ crontab -l
# m h  dom mon dow   command
*/1 * * * * echo "pipipipipipippip"
```

---

### Post by cgjones on 2006-04-21
Are you fully logged in as root, or are you using su or sudo. According to the man page for crontab, su can confuse crontab. They advise that you explicitly specify the user whose crontab you want to edit.

---

### Post by yyagol on 2006-04-21
OK i did su -
i will try login as root
and to run a simple task like echo to see if it works.
when i used older version of ubuntu 5.04 it worked charming.
by the way here is the script . it check if ther is a connection
and if not then it run the script to connect.
```
#!/bin/bash
ping -c 1 -w 5 google.com > /dev/null 2> /dev/null && P="OK" || P="FAIL"

if [ "$P" == "FAIL" ]; then
        /etc/init.d/internet-connect.sh
        exit 0;
fi

```

---

### Post by yyagol on 2006-04-24
any 1 ...

---

### Post by cgjones on 2006-04-24
Were you logged in as root, or were you using su or sudo?

---

### Post by yyagol on 2006-04-28
When i logged as root with no X

---

### Post by cgjones on 2006-04-28
So you have enabled the root account on Ubuntu? I'm not at my Ubuntu machine right now, so I'm not sure if Ubuntu even has these directories, but you could try copying the script to one of the cron folders in /etc. For example, if you want the script to run every hour, do this:
```

cp *scriptname* /etc/cron.hourly

```
Looking at the script again makes me think this is something you would only want to run at startup, but I'm not sure of your exact situation.

---

### Post by zod on 2006-04-28
I got the same problem and will follow closely this thread to see if any can give a solution even I modify manually my /etc/crontab but this does't work for me. Now I see the file without modifications I made.   Is this file generated automatically for example at boot time???? I am asking because ins SuSE linux for example the http.conf is regenerated every time the system starts and the persistent modifications must be placed in /etc/sysconfig/apache. for me there is not explanation about this file remains the same as was installed on my system

Conclusion my cron ignores all crontab installed on my system even if is root who's installing it

---

### Post by zod on 2006-04-28
mmm copying the scripts to /etc/cron.hourly that script is executed by anacron see /etc/crontab and you'll see why

---

### Post by yyagol on 2006-04-30
Well i could use ancron but it would be in a 55 min delay couse
if i am runing a server i want to be shour that i have connection all time
 i can skip cron and do a "while" loop that would go forever but it would
take resources and i find it stupid to to so. i see that i'm not the only 1 
that have this problem so mabye it is not the way i install my ubuntu
(i'v upgradeed from Breezy ).
i am going to try a fresh install of breezy to see is the problem remain
or if it's something to do with Dapper,
i will let you know.
today it hapend to me while i was at work the internet connection fail.
ther was nothing i could do about it from work. that is why i need cron to work.

---

### Post by yyagol on 2006-05-01
After a fresh install of Breezy cron is working when i test it as user
this is what i did :

* * * * * yyagol echo "test">>/home/yyagol/test

it worked but when i try to run cron to do a **root** job
it just did'nt do it :

* * * * * root /root/check-connection

i added this task when login as **root** not as suso/su
How can i run this script as root crontab for all users ????

---

### Post by yyagol on 2006-05-02
I found the problem !!!!!
it seems that cron got its private PATH located at /etc/crontab

when i cat /etc/crontab i saw this :
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

in my script i used ifconfig and it's located in /sbin thats why it did'nt work
i found it when i log cron:
```
root@var32:/home/yyagol# crontab -l
*/3 * * * * /root/check-connection>>/var/log/my-cron.log 2>&1
```
:-D ;)

---

