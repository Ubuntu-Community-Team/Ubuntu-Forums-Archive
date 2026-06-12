---
title: "how to solve this &quot;Checking for corrupt, not cleanly closed and upgrade needing table"
date: 2009-12-22
forum: General Help
---

### Post by snake_eyes on 2009-12-22
Hello,

Every time I restart the mysql I'm getting this error message "Checking for corrupt, not cleanly closed and upgrade needing tables" so how I can solve the problem id exists?

Here is the output:
> 
james@james-laptop$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
 * Starting MySQL database server mysqld                                                                                                              [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.


---

### Post by itang sanjana on 2009-12-22
Hello, someone said "It's not an error! It's just mysqld telling you what it is doing .." see [http://ubuntuforums.org/showthread.php?t=598657](http://ubuntuforums.org/showthread.php?t=598657) HTH

---

### Post by snake_eyes on 2009-12-22
> **itang sanjana said:**
> Hello, someone said "It's not an error! It's just mysqld telling you what it is doing .." see [http://ubuntuforums.org/showthread.php?t=598657](http://ubuntuforums.org/showthread.php?t=598657) HTH

mysql teeling me right, but he said "FIXED please delete thi smessage"
so I guest there is an solution to disappear this kind of messages :(

so is there anything I must doing it in order to avoid such as this message?

---

### Post by itang sanjana on 2009-12-22
Or maybe /var/log/syslog could clear things up? ```
grep mysql /var/log/syslog | less
```

---

### Post by snake_eyes on 2009-12-22
> **itang sanjana said:**
> Or maybe /var/log/syslog could clear things up? ```
less /var/log/syslog | grep mysql
```

for what this command?

---

### Post by iponeverything on 2009-12-22
It is not an error. 

Feedback when starting a service is good. 

If you don't want feedback redirect STDOUT and STDERR to /dev/null/

---

### Post by itang sanjana on 2009-12-22
> **snake_eyes said:**
> for what this command?

Sorry, I mean ```
grep mysql /var/log/syslog | less
```
To see any warning/messages. See [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Also, iponeverything suggestion good to implementing.

---

