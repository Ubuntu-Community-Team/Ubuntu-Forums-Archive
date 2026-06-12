---
title: "sudoers just does not work"
date: 2009-08-14
forum: General Help
---

### Post by teropita on 2009-08-14
I am working on a 9.04 system.

My ultimate goal is to have a script start up and run when the machine boots. I have tried many ways using init.d and also using rc.local but although the script starts it does not keep running. I am fairly sure it is a permissions issue.

The script is called mailAlarm.sh and it is an expect script (it calls expect) and it also calls telnet.

I have tried editing sudoers, but the things I tried did not help.

I then thought maybe I have a fundamental misunderstanding of how sudoers works. So as a test I tried the following.

I added 

username teropita = NOPASSWD: /etc/init.d/mailAlarm.sh

to sudoers, I then rebooted the machine.

I log in as teropita, check that mailAlarm.sh is not running, type sudo /etc/init.d/mailAlarm.sh and Enter.

I then get asked for my password, I thought that adding the line above into sudoers would mean that user teropita would not need to supply a paasword to run the specific script with sudo priveleges.

---

### Post by michy99 on 2009-08-14
This is the line you want:```
teropita ALL=NOPASSWD: /etc/init.d/mailAlarm.sh
```I hope you are using visudo to edit the sudoers file.

---

### Post by vidak on 2009-08-14
Did you try editing the sudoers file with 
```
sudo visudo
```
?

---

### Post by stlsaint on 2009-08-14
bootinto recovery and use
"adduser teropita admin"
after reboot you should be able to either change paswd or get rid of it!!

---

### Post by michy99 on 2009-08-14
> **stlsaint said:**
> bootinto recovery and use
"adduser teropita admin"
after reboot you should be able to either change paswd or get rid of it!!

That has nothing to do with the question. The poster is obviously already a member of admin.

---

### Post by stlsaint on 2009-08-14
sorry maybe i misunderstood issue...will read again and offer advice if can!!

---

### Post by kerry_s on 2009-08-14
> **teropita said:**
> I am working on a 9.04 system.

My ultimate goal is to have a script start up and run when the machine boots. I have tried many ways using init.d and also using rc.local but although the script starts it does not keep running. I am fairly sure it is a permissions issue.

The script is called mailAlarm.sh and it is an expect script (it calls expect) and it also calls telnet.

I have tried editing sudoers, but the things I tried did not help.

I then thought maybe I have a fundamental misunderstanding of how sudoers works. So as a test I tried the following.

I added 

username teropita = NOPASSWD: /etc/init.d/mailAlarm.sh

to sudoers, I then rebooted the machine.

I log in as teropita, check that mailAlarm.sh is not running, type sudo /etc/init.d/mailAlarm.sh and Enter.

I then get asked for my password, I thought that adding the line above into sudoers would mean that user teropita would not need to supply a paasword to run the specific script with sudo priveleges.


/usr/local/bin is the place to put personal scripts.
is it made to run as a daemon, why would you expect the script to keep running?

sounds to me like you need to put it in the right place, only certain paths are checked for executables.(PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin")

then set up a cron job to have it run when you want.
sudo crontab -e

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

you know, just put your script /etc/cron.hourly & it will run all on its own.

---

### Post by teropita on 2009-08-14
Thanks all,

To answer some questions:

yes I am using sudo visudo to edit sudoers.

I tried 

```
teropita ALL=NOPASSWD: /etc/init.d/mailAlarm.sh

```

it did not work

I tried ```
ALL ALL = NOPASSWD:/etc/init.d/mailAlarm.sh

```

and it did work I am now no longer prompted for a password. So I now know that sudoers does work I can move on to solving the rest of the problem.

I have the script in the /etc/init.d directory as I want it to start on boot up. The script starts "expect" and stays running while waiting for data to come to it over a Telnet connection. It works fine if I start it manually while logged on as a user.

On bootup the script starts but does not keep running. Not sure what my problem is now.

---

