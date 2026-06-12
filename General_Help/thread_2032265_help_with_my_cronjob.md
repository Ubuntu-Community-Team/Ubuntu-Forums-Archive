---
title: "help with my cronjob"
date: 2012-07-23
forum: General Help
---

### Post by discord on 2012-07-23
I'm trying to run wget via a cronjob on ubuntu server 12.04 LTS (GNU/Linux 3.2.0-25-virtual x86_64). It seems that via syslog it that the cronjob is run, however the output file from wget isn't created. 

If I run the same wget command manually, the file is created. 


[SIZE="3"]the cronjob itself:[/SIZE]


```

crontab -e


# m h  dom mon dow   command
00 05 * * Sun wget http://private.ip/ -O /home/ubuntu/store/`date +%s`

00 08 * * Sun /usr/bin/killall wget
```




[SIZE="3"]relevant parts of the syslog show that the cron jobs execute:[/SIZE]


```
Jul 22 05:00:01 private.ip2 CRON[6104]: (ubuntu) CMD (wget http://private.ip/ -O /home/ubuntu/store/`date +)

Jul 22 08:00:01 private.ip2 CRON[6467]: (ubuntu) CMD (/usr/bin/killall wget)
```


[SIZE="3"]when i run the wget code from the terminal via the ubuntu user account it works:[/SIZE]

```
ubuntu@ip-10-245-74-62:~$ wget http://private.ip/ -O /home/ubuntu/store/`date +%s`
--2012-07-23 18:44:33--  http://private.ip
Resolving private.ip (private.ip)... private.ip,private.ip
Connecting to private.ip (private.ip)|private.ip... connected.
HTTP request sent, awaiting response... 200 No headers, assuming HTTP/0.9
Length: unspecified
Saving to: `/home/ubuntu/store/1343069073'

    [                                                <=>                                             ] 391,704     56.4K/s              ^C

ubuntu@private.ip2:~$ ls -lah /home/ubuntu/store/
total 404K
drwxrwxr-x 2 ubuntu ubuntu 4.0K Jul 23 18:44 .
drwxr-xr-x 6 ubuntu ubuntu 4.0K Jul 23 18:41 ..
-rw-rw-r-- 1 ubuntu ubuntu 396K Jul 23 18:44 1343069073



```



Am I having a permissions error, because the cron user doesn't own the store folder, or is it something else?

---

### Post by Habitual on 2012-07-23
maybe try...
```
00 05 * * Sun wget http://private.ip/ -O /home/ubuntu/store/$(date +%s)
```should work.

edit:
Oops: "perm error" - sure it will matter, who owns the /home/ubuntu/store directory?/```
 ls -ld /home/ubuntu/store/
``` and who is running the script.

---

### Post by papibe on 2012-07-23
Hi discord.

crontab uses the character **%** as an special character (it replaces it with a newline).

Escape the character with a **\**, and you'll be fine.

BTW, I'd recommend using a more up-to-date syntax for the execution by using $() instead of back-ticks:
```
$(date +\%s)
```
Hope it helps, and let us know how it goes.
Regards.

---

### Post by sanderj on 2012-07-23
> **papibe said:**
> 
BTW, I'd recommend using a more up-to-date syntax for the execution by using $() instead of back-ticks:
```
$(date +\%s)
```


Oh. I didn't know that. Is the $(...) safer/better than `...` ? Not bound to a certain shell?

---

### Post by uylug on 2012-07-23
Simple tip:

Use full paths, ie **/usr/bin/wget** instead of **wget**

Can save you a headache, or two.

---

### Post by discord on 2012-07-23
Thanks for the help. I believe my problem was due to not escaping the % sign. It is working !

---

### Post by papibe on 2012-07-23
Oops, too slow.


> Great :)

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")) when you have the chance.

Regards

---

