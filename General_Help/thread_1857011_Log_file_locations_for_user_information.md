---
title: "Log file locations for user information"
date: 2011-10-09
forum: General Help
---

### Post by gatorguy on 2011-10-09
This forum has been really helpful in finding information that I haven't been able to find via searches. Thanks in advance for any info.

I'm trying to find the following information on a Ubuntu 10.10 system that has been for all intensive purposes, "hacked" into and am looking for the log files for Ubuntu that would give me this information. Unfortunately I'm fairly new to Linux and haven't been able to find the equivalent to Windows System & Security logs. Could anyone point me to the log files that would provide me with the following information?


* How many actual user accounts are on the machine (typically the local users system admin tool would give you this info on Windows) and how many times each user has logged on to the computer (typically a Windows security log would have all the logon and logoff events as long as auditing was turned on with date/time stamps)

* Who was the first & last user to logon and from what location (I know that in the Windows security logs they give you an IP address that the user connected from)

* How many users should be able to run as a super user (i.e. root user)?

Thanks in advance for any info,
Gatorguy

---

### Post by MG&amp;TL on 2011-10-09
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

typically /var/log is a good place to look.

---

### Post by MG&amp;TL on 2011-10-09
```
who
```gives who is currently logged on.

/etc/sudoers isn't really very helpful, but it lists root users.
/etc/passwd lists all accounts.

---

### Post by ajgreeny on 2011-10-09
This is very clunky, but may give you an idea and may also be able to be refined a lot more than I am suggesting here.  This is also assuming you mean actual user account holders, ie those who have **/home/<*username*>** folders on the filesystem somewhere, and not everything listed in /etc/passwd.

Have a look at the use of grep in terminal, and in particular ```
grep -R /home/ /var/log/
``` the output of which will need to be searched more deeply, perhaps, but will tell you a lot about users and their recent logged activities.  If you want info on one particular user you can use ```
grep -R /home/*username* /var/log/
``` and of course you can find all local users with ```
ls /home
``` Unfortunately grep can not search the archived logs in /var/log, but this a start.

---

### Post by gatorguy on 2011-10-09
Thanks for all the information! I'm using both of your post replies to look up information now.

Gatorguy

---

### Post by gatorguy on 2011-10-09
When looking through the etc\passwd file, how do you differentiate as to which accounts are actual user accounts (created by a root user for a person to use) and which ones are system accounts?

I'm reading through various web sites (i.e. [http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)that](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)that) do give me information on how to interpret each field and pulled the file into a spreadsheet but don't see how I can distinguish between a system and a user account.

Thanks in advance for any feedback,
Gatorguy

---

### Post by gatorguy on 2011-10-09
My guess is that user accounts are the only accounts listed in the etc/passwd file that have a home directory of "/home/Username". If that is the case the only question I have is why I see the user "syslog" that has a Home Directory of /home/syslog included in that group?

Thanks,
Gatorguy



*****************************************************************
Re: Log file locations for user information 

--------------------------------------------------------------------------------

When looking through the etc\passwd file, how do you differentiate as to which accounts are actual user accounts (created by a root user for a person to use) and which ones are system accounts?

I'm reading through various web sites (i.e. [http://www.cyberciti.biz/faq/underst...e-format/)that](http://www.cyberciti.biz/faq/underst...e-format/)that) do give me information on how to interpret each field and pulled the file into a spreadsheet but don't see how I can distinguish between a system and a user account.

Thanks in advance for any feedback,
Gatorguy

---

### Post by MG&amp;TL on 2011-10-10
No hard and fast rule, but all the actual user accounts seem to be at the bottom, and the others (that are system accounts) tend to have 'system' names, not 'Bob' 'Administrator' 'Fred' or, in your case, 'hacked!'

Also google each of them. If there's a manpage hit, or 'how to', it's likely to be universal.

---

### Post by gatorguy on 2011-10-10
Thanks again for all the information. I'm trying to search the forum and web before posting.

Gatorguy

---

### Post by MG&amp;TL on 2011-10-10
> **gatorguy said:**
> Thanks again for all the information. I'm trying to search the forum and web before posting.

Gatorguy


I didn't mean, 'google it before coming here' ! :)  That would be nasty.

I am interested now, are you making any progress?

---

### Post by gatorguy on 2011-10-10
Too funny! I wasn't responding to the comment about "to google each user", I just didn't want you to think I was going here before searching the forums first.

The hacked system I'm looking at is for a digital forensics graduate course so I'm only trying to get general info to help me research the problem. They provided us with a hacked VM (virtual machine) and we're supposed to find out information about the system, users, and then details about the actual incident (I'm not that far yet). Luckily I don't get paid to support Unix/Linux systems for my day job!  :)

Of the 43 user accounts listed I have identified a much smaller number using the information you provided earlier and I also have a test VM I am using to compare with the "hacked" system. That new Ubuntu build gave me a good idea of what accounts are created from the get go. I now am working on identifying information such as who the first and last user was to logon and also identifying any users that did not show any activity. I'm going to work on trying to find any log files tonight (I try not to work on any school work during the day while working) that will give me that information.

Sorry for the long winded post, but you asked.

Thanks again for all the assistance. It's been very helpful.
Gatorguy

---

### Post by SeijiSensei on 2011-10-10
Ubuntu creates user accounts starting with ID 1000.  All the two-digit and three-digit IDs are system accounts.

I seem to have a /home/syslog entry for the syslog user as well (on a brand-new Kubuntu 10.10 installation).  I suspect that's a coding error of some kind.  The syslog user has /bin/false as a shell, which means it doesn't support real logins.  Not all system accounts have /bin/false as a shell because some processes like the Apache web server, which runs as user www-data, need to do things like write logs.

To answer your original question, logins and logouts are written to /var/log/auth.log.  You need to be root to view this file.  Logs are rotated weekly, so last week's log is called /var/log/auth.log.1 and so forth.

---

### Post by gatorguy on 2011-10-10
SeijiSensei,

Thanks for the info. I'll dig through those logs tonight to find more information. One thing I like about Linux in general is how helpful the user community is. It is a far cry from what I see on some of the forums I use for Microsoft backend system (i.e. Hyper-V, Exchange, SQL, etc...)

Thanks again for the info. The course has been very cool so far. Our last project was to take a Wireshark capture dump and determine what type malicious activity was occurring and to determine from the dump whether any attempts were successful and where the traffic originated from (and of course what systems were affected).

Gatorguy

---

### Post by SeijiSensei on 2011-10-10
> **gatorguy said:**
> One thing I like about Linux in general is how helpful the user community is. It is a far cry from what I see on some of the forums I use for Microsoft backend system (i.e. Hyper-V, Exchange, SQL, etc...)

It's easier to be helpful if everything is out there in plain view; that's not the Windows way.

---

### Post by MG&amp;TL on 2011-10-10
Partly why I switched. It annoys me not knowing what goes on 'behind closed .dlls'

---

### Post by gatorguy on 2011-10-10
When reviewing an entry from what I think is where a user logs on (the entry below is from a test user I created on my test VM), I noticed that at the end of the entry it lists "uid=0" and thought initially this was the UserID of the user but when looking at my logon to the system and the other accounts on the "hacked" VM, they all have "uid=0".

**Oct 10 21:34:15 Ubuntu11 gdm-session-worker[2795]: pam_unix(gdm:session): session opened for user testuser by (uid=0)**

I've been trying to find a site that explains each section of the entry. So far I've deducted the following but am unsure on the other components of the entry:

**Date/time ComputerName Process[PID]: **

Thanks for any info.
Gatorguy

---

### Post by SeijiSensei on 2011-10-12
```
session opened for user testuser by (uid=0)
```

"by (uid=0)" means the session was started by a root-owned process, not that user testuser has uid 0.

---

### Post by MG&amp;TL on 2011-10-12
PID is a tag-line for processes. If you run:

 ```
top
``` you can see a lot of processes, their owners and their PIDs. If you kill a process, you can reference it by its PID. 

Thus logging in for testuser created a PID for his login.

And I daresay Date/Time is self-exlanatory and Computer name would be the computer. In your case, probably gatorguy-desktop. Or whatever. The terminal prompt will have:

```
gatorguy@pcname-desktop/laptop:~$_
```

---

