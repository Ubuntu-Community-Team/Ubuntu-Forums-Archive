---
title: "How to remove mysql from startup"
date: 2010-05-22
forum: General Help
---

### Post by ganeshmallyap on 2010-05-22
Hi all,

I have installed mysql server on my Ubuntu Lucid AMD64 desktop.  I need to run this service only on need.  So I prefer not to have this in startup. So I did the following -

1. Deactivated the row entry by name "mysql" from application BootUp-Manager.  
2. Run the application sysv-rc-conf and unchecked the checkboxes for all run levels.
3. Run the command "sudo update-rc.d -f mysql remove".  Execution completed successfully.
4. Run the command - "sudo service mysql stop".  In return I got a message "mysql stop/waiting".
5. Restarted the desktop.

Now when I read through the task manager, I still see a process by name "mysqld" running.  I ran the command as mentioned in # 4 above and got the same response.  I wanted to know how do I turn off mysql service running from startup permanently.  But I still need to run it as and when required.  

Thanks in advance.  

Regards
Ganesh

---

### Post by James78 on 2010-05-22
I'd sure love to see how to fix this, I tried quite a few things to stop automatic MySQL startup... Seeing as I'm not using it at the moment (I figure I'll just start Apache2 and MySQL when I actually need them, otherwise they're hogging bootup time, and system resources).

---

### Post by v1ad on 2010-05-22
sudo service mysqld stop
sudo chkconfig mysqld off


service stops it
chkconfig makes sure it wont turn on again
sudo apt-get remove mysqld-server (if u want to remove it)

---

### Post by James78 on 2010-05-22
Funny, I did chkconfig and it already said it was off... And I still get it still starts up.. By the way, it's chkconfig mysql off... :)

---

### Post by v1ad on 2010-05-22
hmm that is weird.

did u check System > Administration >  Startup-applications  ? maybe disable it there.

---

### Post by James78 on 2010-05-22
Nope, also not there either! That's why this is such a mystery too me haha. :P

---

### Post by v1ad on 2010-05-22
lol well run those commands again restart and see if it is still running.

---

### Post by Aearenda on 2010-05-22
I don't know the approved way of doing this in 10.04, but what I did was to edit the file /etc/init/mysql.conf (i.e., ALT+F2 and run gksudo gedit /etc/init/mysql.conf) and comment out the two lines as shown below:```
#start on (net-device-up
#          and local-filesystems)
```
Then save the file, of course.

This file will be updated if mysql is updated, and you may need to repeat the change.

---

### Post by vanessa on 2011-01-08
I've tried everything on this thread and the only thing that worked was editing the file as well.

I'm using 10.10.

So I'm just upping the topic to ask if anyone has found a cleaner solution already.

---

