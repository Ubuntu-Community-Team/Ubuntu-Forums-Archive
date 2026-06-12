---
title: "Output of last command"
date: 2011-05-28
forum: General Help
---

### Post by techbrainless on 2011-05-28
Hi All, 

the following is the output of last command

```
techbrainless@com-techbrainless:~$ last
techbrainless   pts/0        :0.0             Sat May 28 09:09   still logged in   
techbrainless   tty7         :0               Sat May 28 08:57   still logged in   
reboot   system boot  2.6.32-21-generi Sat May 28 08:56 - 10:49  (01:52)    
techbrainless   pts/0        :0.0             Tue May 24 10:28 - 10:30  (00:01)    
techbrainless   pts/4        :0.0             Mon May 23 15:09 - crash (4+17:46)   
techbrainless   pts/2        :0.0             Mon May 23 11:08 - 10:28  (23:19)    
techbrainless   pts/1        :0.0             Mon May 23 10:57 - 10:28  (23:30)    
techbrainless   pts/0        :0.0             Mon May 23 10:54 - 10:28  (23:34)    
techbrainless   tty7         :0               Mon May 23 10:51 - crash (4+22:04)   
reboot   system boot  2.6.32-21-generi Mon May 23 10:51 - 10:49 (4+23:57)   
techbrainless   pts/2        :0.0             Mon May 23 10:43 - down   (00:07)    
techbrainless   pts/0        :0.0             Mon May 23 09:02 - down   (01:48)    
techbrainless   tty7         :0               Mon May 23 08:38 - down   (02:12)    
reboot   system boot  2.6.32-21-generi Mon May 23 08:38 - 10:51  (02:12)    
techbrainless   pts/0        :0.0             Tue May 17 08:52 - 08:37 (5+23:44)   
techbrainless   pts/0        :0.0             Tue May 17 08:43 - 08:44  (00:00)    
techbrainless   pts/2        :0.0             Mon May 16 17:52 - 08:43  (14:50)    
techbrainless   pts/1        :0.0             Mon May 16 12:33 - 08:43  (20:10)    
techbrainless   pts/0        :0.0             Sun May 15 08:57 - 17:58 (1+09:00)   
techbrainless   tty7         :0               Sun May 15 08:48 - down  (7+23:48)   
reboot   system boot  2.6.32-21-generi Sun May 15 08:45 - 08:37 (7+23:52)   
techbrainless   pts/1        :0.0             Mon May  9 17:55 - 17:44 (1+23:49)   
techbrainless   pts/1        :0.0             Sun May  8 09:29 - 17:55 (1+08:25)   
techbrainless   pts/0        :0.0             Sun May  8 09:12 - 17:55 (1+08:42)   
```

I need someone to explain to me the explanation for the columns of last command output ?

for example I dont understand the following row
```
reboot   system boot  2.6.32-21-generi Sat May 28 08:56 - 10:49  (01:52)    
```

---

### Post by Pand5461 on 2011-05-28
I could only find info from the manpage:
```
The pseudo user reboot logs in each time the system is rebooted. Thus last reboot will show a log of all reboots since the log file was created.
```

---

### Post by techbrainless on 2011-05-28
Thanks Pand5461 for your reply , 

I am sorry , frankly i did not get you what are going to say!!!

In a brief could you explain the following the line
```
reboot   system boot  2.6.32-21-generi Sat May 28 08:56 - 10:49  (01:52)
```

---

### Post by Pand5461 on 2011-05-28
Honestly i've seen the command the first time. But OK, as far as i can understand:
first column is the username - i.e. user is reboot (which means system was rebooted)
second column is the name of terminal the user connected to - system boot
third column is Hostname for remote login, or kernel version for run-level messages
then go login time and (?)the time log entry was made.

So, long story short, this line means you rebooted your computer at 8:56 on May 28.

---

### Post by techbrainless on 2011-05-28
Thanks Pand5461 for your reply ,

>  So, long story short, this line means you rebooted your computer at 8:56 on May 28.     I have understood that but what are the last 2 columns ? 
```
10:49  (01:52)
```

---

### Post by Pand5461 on 2011-05-28
These are time of logout and session duration - i think it's time of the next reboot or current time for the last "reboot" session.

---

