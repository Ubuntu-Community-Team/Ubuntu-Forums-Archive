---
title: "crontab help"
date: 2009-07-07
forum: General Help
---

### Post by pramathesh on 2009-07-07
Guys I want my laptop to shutdown daily @ 0745hrs. Can anyone here help me with the crontab entry??

---

### Post by credobyte on 2009-07-07
Terminal :
```
crontab -e
```

Add :
```
45 07 * * * sudo shutdown -h now
```

---

### Post by pramathesh on 2009-07-07
I did the same and just to test I set my system time as 7:44 it doesn't work as of now any help??

---

### Post by spibou on 2009-07-07
You edit /etc/crontab and you add a line

```
45 07 * * *   root    shutdown -p now
```

---

### Post by pramathesh on 2009-07-07
> **spibou said:**
> You edit /etc/crontab and you add a line

```
45 07 * * *   root    shutdown -p now
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
45 07 * * *   root    shutdown -p now
#


This is how my crontab looks like now but it still doesn't work!! :((

---

### Post by credobyte on 2009-07-07
Add this line ( replace time ) to your crontab and let us know if it works or not ( should create a new file on your Desktop ) :
```
45 07 * * * echo "Message delivered!" >> $HOME/Desktop/cronmsg.txt
```

---

### Post by pramathesh on 2009-07-07
> **credobyte said:**
> Add this line ( replace time ) to your crontab and let us know if it works or not ( should create a new file on your Desktop ) :
```
45 07 * * * echo "Message delivered!" >> $HOME/Desktop/cronmsg.txt
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
45 07 * * *   root    shutdown -p now
45 07 * * * echo "Message delivered!" >> $HOME/Desktop/cronmsg.txt
#


this is how the crontab looks like now

---

### Post by spibou on 2009-07-07
Try creating the following file , let's call it $HOME/script
```
#!/bin/sh

shutdown -p now > /tmp/error-log 2>&1
```
Now you do```
chmod 555 $HOME/script
```
And then in /etc/crontab you replace the line```
45 07 * * * root shutdown -p now
```
with the line ```
45 07 * * * root .../script
```
where ... should be replaced by the value of $HOME. If for example $HOME is /home/myusername then in /etc/crontab you put the line```
45 07 * * * root /home/myusername/script
```
After this you try again to see if the computer gets shut down at the right time. If not post here the content of /tmp/error-log

Apart from that I have another suspicion. It may be that changing the system time confuses the cron daemon. So when testing it don't change the system time but instead change the shutdown time to a few minutes after you do the above. So if for example you have everything ready for the test at 15:00 then you put inside /etc/crontab the line```
04 15 * * * root /home/myusername/script
```which will try to shutdown the computer at 15:04.

---

### Post by pramathesh on 2009-07-07
chmod: cannot access `/home/pramathesh/script': No such file or directory


sorry for being such a newbie! :(

---

### Post by spibou on 2009-07-07
Do
```

cat << EOF > $HOME/script
#!/bin/sh

shutdown -p now > /tmp/error-log 2>&1
EOF
``` and then the steps I mentioned in the previous post starting with chmod.

---

