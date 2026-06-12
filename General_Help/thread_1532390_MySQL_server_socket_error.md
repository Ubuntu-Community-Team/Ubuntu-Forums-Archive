---
title: "MySQL server socket error"
date: 2010-07-16
forum: General Help
---

### Post by porchrat on 2010-07-16
Hi all

Been a while since I've needed to post here. Either I'm getting better or Ubuntu is getting easier :)

Trying to move my MySQL databases over to a new 10.04 install (old 8.04 install crashed quite unexpectedly). Part of this move is that I need the MySQL datadir to run on a separate drive (i.e. not in the standard /var/lib/mysql) and so I move it.

I have followed my standard procedure for moving the datadir. A pretty good guide for what I do is located [here]("http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html").

I do pretty much what it says except that I don't remove the ib* stuff because as far as I recall it is required for InnoDB stuff. At the moment I use only MyISAM but still no need to cripple the thing. I also make backups all along as I edit instead of just editing... whcih I know is strange considering I just comment out lines instead of deleting them but you never can be too careful.

When I perform the above operation from the ubuntugeek reference my MySQL is fine and I can login and do my thing. Created a few databases just to make sure it was in fact reading the new datadir and it is. No problem.

The minute I restart and try to login again I get this:
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

What is going on here?

---

### Post by DaithiF on 2010-07-16
Hi,
you would get that message trying to connect to a mysql instance that  isn't running.  
what does **sudo service mysql status **say?

you can start it manually of course:
```
sudo service mysql start

```
and then you need to figure out why its not starting at boot time.  Check in /var/log/syslog for possible error messages

---

### Post by porchrat on 2010-07-17
> **DaithiF said:**
> Hi,
you would get that message trying to connect to a mysql instance that  isn't running.  
what does **sudo service mysql status **say?

you can start it manually of course:
```
sudo service mysql start

```
and then you need to figure out why its not starting at boot time.  Check in /var/log/syslog for possible error messages

Thanks for the response. Definitely useful advice that I am going to need moving forward with this. At this point I think the problem is more fundamental.

I tried removing the mysql-server-5.1 package last night and synaptic crashed. Going to try forcing it through apt-get now but I get the feeling there is something wrong with the 10.04 install (the install is only about 3 days old).

---

### Post by WorMzy on 2010-07-17
Try touching the file.
```
sudo touch /var/run/mysqld/mysqld.sock
```
then change the ownership to mysql and the permissions to rwx for everyone
```
sudo chown mysql:mysql /var/run/mysqld/mysqld.sock
sudo chmod 777 /var/run/mysqld/mysqld.sock
```

---

### Post by porchrat on 2010-07-17
> **WorMzy said:**
> Try touching the file.
```
sudo touch /var/run/mysqld/mysqld.sock
```
then change the ownership to mysql and the permissions to rwx for everyone
```
sudo chown mysql:mysql /var/run/mysqld/mysqld.sock
sudo chmod 777 /var/run/mysqld/mysqld.sock
```

This is interesting. What purpose would touching the file have towards solving the restart issue?

I understand the permissions part but remember that before I restarted the system MySQL was able to access the new datadir on the other drive. Surely if permissions were messed up it wouldn't be able to access the directory even before a restart?

Or am I missing something?

---

### Post by porchrat on 2010-07-17
OK as a quick update I have reinstalled Ubuntu 10.04 and I really do think that something went wrong with the last installation. When I installed last I was for some reason unable to access the repositories for an "apt-get update" but I had something like 250MB of upgrades waiting. Did the upgrades and another 162MB all of a sudden materialised out of thin air because all of a sudden the system could access the repos.

This time around things were different and the system was able to update straight away with all relevant updates in half the time (far fewer MBs downloaded).

I have just made the changes to /etc/mysql/my.cnf and /etc/apparmor.d/usr.sbin.mysqld reflecting the location of the new datadir.

I have reloaded AppArmor and started MySQL again.

MySQL status is:
> mysql start/running, process 2195

I'm going to try restart the system and let those of you who are reading this thread what happens. Fingers crossed...

---

### Post by porchrat on 2010-07-17
Hey hey!

It is working. Did everything exactly as I did with my previous 10.04 install.

There must have been something wrong with the previous install which would explain the initial lack of connectivity with the repos and the inability to remove mysql-server-5.1!

Well thanks to the brave souls that attempted to help me resolve this issue it is much appreciated.

As a side note though to the second suggestion of trying a "touch" and permissions change could you please explain that to me. Just as some additional information to help me in the future when handling files in Linux.

Some sound advice here. Especially checking the logs. I should have done that initially before attempting to remove the MySQL packages. In the future I will try to do that. Thanks again. :)

Anyway I hereby officially mark this thread [SOLVED]!

---

### Post by WorMzy on 2010-07-17
The touch command just makes a blank file, and chowning it to mysql gives the mysql user/process the ability to do whatever it wants with it. If the file doesn't exist, and a process being run under the mysql user requires it (for whatever reason), then creating the file and giving it to the mysql user will allow it to use the file for whatever it needs it for.

I've had the same message thrown at me before, and touching that file has always worked for me, so I figured it may work for you too.

---

### Post by porchrat on 2010-07-19
> **WorMzy said:**
> The touch command just makes a blank file, and chowning it to mysql gives the mysql user/process the ability to do whatever it wants with it. If the file doesn't exist, and a process being run under the mysql user requires it (for whatever reason), then creating the file and giving it to the mysql user will allow it to use the file for whatever it needs it for.

I've had the same message thrown at me before, and touching that file has always worked for me, so I figured it may work for you too.

Ah that makes sense. I will keep that in mind for the future.

Though if the file does exist then touch doesn't create a blank file it just updates the timestamps. that is what I thought anyway.

Thanks again.

---

