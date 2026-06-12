---
title: "ssh prog"
date: 2010-01-12
forum: General Help
---

### Post by endoglastic on 2010-01-12
Ok, ssh works fine on root but when i log into my other account, the ssh doesn't work, it just times out when i putty it.
 
I used this to try and start it from terminal in my reg acc, and then as the su.
 
sudo /etc/init.d/ssh start
 
After that didn't work i did this
 
sudo apt-get remove openssh-server
sudo apt-get install openssh-server
sudo /etc/init.d/ssh start
 
and still nothing. I have no clue why it only works on root and no other accounts.

---

### Post by manosx on 2010-01-12
what do you mean?
only root can run it, but once it's running you can log in to any account of the computer.

---

### Post by endoglastic on 2010-01-12
Ok here is the deal. It's probably always been like this but... I restarted the computer, logged into my acc named sam, tried to ssh it no luck. Logged out of sam, then i logged into root. Then i ssh'd it and boom perfect. Logged out of root, and back into sam, tried to ssh it, and it does not work, putty times out, only when i am logged into root in the computer does ssh work. Its like it wont start in my other account called sam even though it says starting blah blah blah.
 
 
But on the flip side......
 
I did this on my other computer, and i am having no problems.

---

### Post by jbird80 on 2010-01-12
Are you trying to ssh into the same machine?

---

### Post by endoglastic on 2010-01-12
> **jbird80 said:**
> Are you trying to ssh into the same machine?
 
Yes its the same machine, i had my brother log in as root, and ssh'd it from my house, works like a charm. I had him then logged out of that and into my other acc sam. Proceeded to ssh it again, and it does not work.

---

### Post by YetAnother on 2010-01-12
Take a look at what your /var/log/auth.log says and post it here.
I am also assuming you didn't tinker with anything in /etc/ssh/sshd_config and /etc/ssh/ssh_config

---

### Post by endoglastic on 2010-01-12
> **YetAnother said:**
> I am also assuming you didn't tinker with anything in /etc/ssh/sshd_config and /etc/ssh/ssh_config
 
Nope all of them are what it comes with when it is installed. And i'm baffled because i set up both of these computers i have one at my house that works fine, but his has a problem.

---

### Post by YetAnother on 2010-01-12
can you login as sam remotley when he is logged in as root. ? Can you login as sam locally via ssh. try ssh sam@locahost  File permissions of his home directory can also cause problems. check iptables -L make sure he did't restrict port 22.

---

### Post by endoglastic on 2010-01-12
> **YetAnother said:**
> can you login as sam remotley when he is logged in as root. ? 
No. Only when i am logged in as root on the actual computer does ssh work.
 
> **YetAnother said:**
>  Can you login as sam locally via ssh. try ssh sam@locahost. 
Locally no, my brother tried it with the internal address and it timed out also. sam@local host does not work. But when the computer is logged on as root and i ssh it i can log onto sam or root.
 
> **YetAnother said:**
> check iptables -L make sure he did't restrict port 22.
I will tell my brother to do that, what do i do if its blocked? The port can be unblocked on root but when you log on another account it can be blocked, interesting.

---

### Post by endoglastic on 2010-01-12
Ok here is what i did on my computer at home, not his.
 
```
sammy@sam-server2:~$ iptables -L
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
sammy@sam-server2:~$ su
Password:
root@sam-server2:/home/sammy# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@sam-server2:/home/sammy#
 

```
 
I don't see anything about port 22 in here.

---

### Post by YetAnother on 2010-01-12
> The port can be unblocked on root but when you log on another account it can be blocked, interesting.
Nah. you can't block incoming ports on per user basis. 

> Take a look at what your /var/log/auth.log says and post it here
Let's try this part again.

---

### Post by endoglastic on 2010-01-12
ok when my bro is at his house again, i will post that when he sends it to me.

---

### Post by endoglastic on 2010-01-12
```
 
Jan 12 00:35:05 Sam-linux-server sshd[26290]: Invalid user vva from 59.37.54.38
Jan 12 00:35:05 Sam-linux-server sshd[26290]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:05 Sam-linux-server sshd[26290]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:07 Sam-linux-server sshd[26290]: Failed password for invalid user vva from 59.37.54.38 port 35900 ssh2
Jan 12 00:35:13 Sam-linux-server sshd[26292]: Invalid user JIRAUSER from 59.37.54.38
Jan 12 00:35:13 Sam-linux-server sshd[26292]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:13 Sam-linux-server sshd[26292]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:15 Sam-linux-server sshd[26292]: Failed password for invalid user JIRAUSER from 59.37.54.38 port 38944 ssh2
Jan 12 00:35:22 Sam-linux-server sshd[26294]: Invalid user dca from 59.37.54.38
Jan 12 00:35:22 Sam-linux-server sshd[26294]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:22 Sam-linux-server sshd[26294]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:24 Sam-linux-server sshd[26294]: Failed password for invalid user dca from 59.37.54.38 port 42076 ssh2
Jan 12 00:35:30 Sam-linux-server sshd[26296]: Invalid user dby from 59.37.54.38
Jan 12 00:35:30 Sam-linux-server sshd[26296]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:30 Sam-linux-server sshd[26296]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:32 Sam-linux-server sshd[26296]: Failed password for invalid user dby from 59.37.54.38 port 45179 ssh2
Jan 12 00:35:39 Sam-linux-server sshd[26298]: Invalid user ntp from 59.37.54.38
Jan 12 00:35:39 Sam-linux-server sshd[26298]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:39 Sam-linux-server sshd[26298]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:42 Sam-linux-server sshd[26298]: Failed password for invalid user ntp from 59.37.54.38 port 48348 ssh2
Jan 12 00:35:48 Sam-linux-server sshd[26300]: Invalid user oro from 59.37.54.38
Jan 12 00:35:48 Sam-linux-server sshd[26300]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:48 Sam-linux-server sshd[26300]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:50 Sam-linux-server sshd[26300]: Failed password for invalid user oro from 59.37.54.38 port 52346 ssh2
Jan 12 00:35:56 Sam-linux-server sshd[26302]: Invalid user gve from 59.37.54.38
Jan 12 00:35:56 Sam-linux-server sshd[26302]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:35:56 Sam-linux-server sshd[26302]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:35:58 Sam-linux-server sshd[26302]: Failed password for invalid user gve from 59.37.54.38 port 55424 ssh2
Jan 12 00:36:05 Sam-linux-server sshd[26304]: Invalid user jpd from 59.37.54.38
Jan 12 00:36:05 Sam-linux-server sshd[26304]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:36:05 Sam-linux-server sshd[26304]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:36:07 Sam-linux-server sshd[26304]: Failed password for invalid user jpd from 59.37.54.38 port 58574 ssh2
Jan 12 00:36:14 Sam-linux-server sshd[26306]: Invalid user jmn from 59.37.54.38
Jan 12 00:36:14 Sam-linux-server sshd[26306]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:36:14 Sam-linux-server sshd[26306]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:36:16 Sam-linux-server sshd[26306]: Failed password for invalid user jmn from 59.37.54.38 port 33509 ssh2
Jan 12 00:36:22 Sam-linux-server sshd[26308]: Invalid user wrioffice from 59.37.54.38
Jan 12 00:36:22 Sam-linux-server sshd[26308]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:36:22 Sam-linux-server sshd[26308]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:36:24 Sam-linux-server sshd[26308]: Failed password for invalid user wrioffice from 59.37.54.38 port 36661 ssh2
Jan 12 00:36:30 Sam-linux-server sshd[26310]: Invalid user listtranslate from 59.37.54.38
Jan 12 00:36:30 Sam-linux-server sshd[26310]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:36:30 Sam-linux-server sshd[26310]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:36:32 Sam-linux-server sshd[26310]: Failed password for invalid user listtranslate from 59.37.54.38 port 39647 ssh2
Jan 12 00:36:44 Sam-linux-server sshd[26312]: Invalid user polina from 59.37.54.38
Jan 12 00:36:44 Sam-linux-server sshd[26312]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 00:36:44 Sam-linux-server sshd[26312]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=59.37.54.38 
Jan 12 00:36:46 Sam-linux-server sshd[26312]: Failed password for invalid user polina from 59.37.54.38 port 42713 ssh2
Jan 12 01:17:01 Sam-linux-server CRON[26318]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 01:17:01 Sam-linux-server CRON[26318]: pam_unix(cron:session): session closed for user root
Jan 12 02:17:01 Sam-linux-server CRON[26328]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 02:17:01 Sam-linux-server CRON[26328]: pam_unix(cron:session): session closed for user root
Jan 12 03:17:01 Sam-linux-server CRON[26337]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 03:17:01 Sam-linux-server CRON[26337]: pam_unix(cron:session): session closed for user root
Jan 12 04:17:01 Sam-linux-server CRON[26347]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 04:17:01 Sam-linux-server CRON[26347]: pam_unix(cron:session): session closed for user root
Jan 12 05:04:22 Sam-linux-server sshd[26359]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:04:24 Sam-linux-server sshd[26359]: Failed password for root from 193.59.150.244 port 39205 ssh2
Jan 12 05:04:31 Sam-linux-server sshd[26361]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:04:33 Sam-linux-server sshd[26361]: Failed password for root from 193.59.150.244 port 39951 ssh2
Jan 12 05:04:40 Sam-linux-server sshd[26363]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:04:42 Sam-linux-server sshd[26363]: Failed password for root from 193.59.150.244 port 40783 ssh2
Jan 12 05:04:50 Sam-linux-server sshd[26365]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:04:52 Sam-linux-server sshd[26365]: Failed password for root from 193.59.150.244 port 41618 ssh2
Jan 12 05:04:59 Sam-linux-server sshd[26367]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:01 Sam-linux-server sshd[26367]: Failed password for root from 193.59.150.244 port 42441 ssh2
Jan 12 05:05:08 Sam-linux-server sshd[26369]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:10 Sam-linux-server sshd[26369]: Failed password for root from 193.59.150.244 port 43128 ssh2
Jan 12 05:05:17 Sam-linux-server sshd[26371]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:19 Sam-linux-server sshd[26371]: Failed password for root from 193.59.150.244 port 43894 ssh2
Jan 12 05:05:26 Sam-linux-server sshd[26373]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:28 Sam-linux-server sshd[26373]: Failed password for root from 193.59.150.244 port 44678 ssh2
Jan 12 05:05:35 Sam-linux-server sshd[26375]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:37 Sam-linux-server sshd[26375]: Failed password for root from 193.59.150.244 port 45539 ssh2
Jan 12 05:05:44 Sam-linux-server sshd[26377]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:46 Sam-linux-server sshd[26377]: Failed password for root from 193.59.150.244 port 46337 ssh2
Jan 12 05:05:53 Sam-linux-server sshd[26379]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:05:56 Sam-linux-server sshd[26379]: Failed password for root from 193.59.150.244 port 47128 ssh2
Jan 12 05:06:03 Sam-linux-server sshd[26381]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=193.59.150.244  user=root
Jan 12 05:06:05 Sam-linux-server sshd[26381]: Failed password for root from 193.59.150.244 port 47941 ssh2
Jan 12 05:17:01 Sam-linux-server CRON[26385]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 05:17:01 Sam-linux-server CRON[26385]: pam_unix(cron:session): session closed for user root
Jan 12 06:17:01 Sam-linux-server CRON[26400]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 06:17:01 Sam-linux-server CRON[26400]: pam_unix(cron:session): session closed for user root
Jan 12 06:25:01 Sam-linux-server CRON[26406]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 06:25:01 Sam-linux-server CRON[26406]: pam_unix(cron:session): session closed for user root
Jan 12 07:17:01 Sam-linux-server CRON[26423]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 07:17:01 Sam-linux-server CRON[26423]: pam_unix(cron:session): session closed for user root
Jan 12 07:30:01 Sam-linux-server CRON[26429]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 07:30:01 Sam-linux-server CRON[26429]: pam_unix(cron:session): session closed for user root
Jan 12 07:35:03 Sam-linux-server sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jan 12 07:35:03 Sam-linux-server sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jan 12 07:35:03 Sam-linux-server sudo:     root : TTY=unknown ; PWD=/ ; USER=sam ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jan 12 08:17:01 Sam-linux-server CRON[26585]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 08:17:01 Sam-linux-server CRON[26585]: pam_unix(cron:session): session closed for user root
Jan 12 09:17:01 Sam-linux-server CRON[26602]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 09:17:01 Sam-linux-server CRON[26602]: pam_unix(cron:session): session closed for user root
Jan 12 10:17:01 Sam-linux-server CRON[26619]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 10:17:01 Sam-linux-server CRON[26619]: pam_unix(cron:session): session closed for user root
Jan 12 11:17:01 Sam-linux-server CRON[26637]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 11:17:01 Sam-linux-server CRON[26637]: pam_unix(cron:session): session closed for user root
Jan 12 12:17:01 Sam-linux-server CRON[26654]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 12:17:01 Sam-linux-server CRON[26654]: pam_unix(cron:session): session closed for user root
Jan 12 13:17:01 Sam-linux-server CRON[26670]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 13:17:01 Sam-linux-server CRON[26670]: pam_unix(cron:session): session closed for user root
Jan 12 14:17:01 Sam-linux-server CRON[26688]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 14:17:01 Sam-linux-server CRON[26688]: pam_unix(cron:session): session closed for user root
Jan 12 14:19:28 Sam-linux-server sshd[26692]: Accepted password for root from 72.193.243.114 port 49860 ssh2
Jan 12 14:19:28 Sam-linux-server sshd[26692]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 14:19:32 Sam-linux-server sshd[26692]: subsystem request for sftp
Jan 12 14:20:29 Sam-linux-server sshd[26692]: pam_unix(sshd:session): session closed for user root
Jan 12 14:20:44 Sam-linux-server sshd[26755]: Accepted password for root from 72.193.243.114 port 49861 ssh2
Jan 12 14:20:44 Sam-linux-server sshd[26755]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 14:20:44 Sam-linux-server sshd[26755]: subsystem request for sftp
Jan 12 14:24:40 Sam-linux-server sshd[26755]: pam_unix(sshd:session): session closed for user root
Jan 12 14:48:25 Sam-linux-server sshd[26820]: Did not receive identification string from 211.35.204.201
Jan 12 14:52:47 Sam-linux-server sshd[26821]: Invalid user a from 211.35.204.201
Jan 12 14:52:47 Sam-linux-server sshd[26821]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:52:47 Sam-linux-server sshd[26821]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:52:49 Sam-linux-server sshd[26821]: Failed password for invalid user a from 211.35.204.201 port 53316 ssh2
Jan 12 14:52:56 Sam-linux-server sshd[26823]: Invalid user a from 211.35.204.201
Jan 12 14:52:56 Sam-linux-server sshd[26823]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:52:56 Sam-linux-server sshd[26823]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:52:57 Sam-linux-server sshd[26823]: Failed password for invalid user a from 211.35.204.201 port 55188 ssh2
Jan 12 14:53:04 Sam-linux-server sshd[26825]: Invalid user a from 211.35.204.201
Jan 12 14:53:04 Sam-linux-server sshd[26825]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:04 Sam-linux-server sshd[26825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:05 Sam-linux-server sshd[26825]: Failed password for invalid user a from 211.35.204.201 port 60274 ssh2
Jan 12 14:53:11 Sam-linux-server sshd[26827]: Invalid user a from 211.35.204.201
Jan 12 14:53:11 Sam-linux-server sshd[26827]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:11 Sam-linux-server sshd[26827]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:13 Sam-linux-server sshd[26827]: Failed password for invalid user a from 211.35.204.201 port 37357 ssh2
Jan 12 14:53:20 Sam-linux-server sshd[26829]: Invalid user a from 211.35.204.201
Jan 12 14:53:20 Sam-linux-server sshd[26829]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:20 Sam-linux-server sshd[26829]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:23 Sam-linux-server sshd[26829]: Failed password for invalid user a from 211.35.204.201 port 43068 ssh2
Jan 12 14:53:29 Sam-linux-server sshd[26831]: Invalid user a from 211.35.204.201
Jan 12 14:53:29 Sam-linux-server sshd[26831]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:29 Sam-linux-server sshd[26831]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:31 Sam-linux-server sshd[26831]: Failed password for invalid user a from 211.35.204.201 port 48724 ssh2
Jan 12 14:53:37 Sam-linux-server sshd[26833]: Invalid user a from 211.35.204.201
Jan 12 14:53:37 Sam-linux-server sshd[26833]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:37 Sam-linux-server sshd[26833]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:39 Sam-linux-server sshd[26833]: Failed password for invalid user a from 211.35.204.201 port 52207 ssh2
Jan 12 14:53:45 Sam-linux-server sshd[26835]: Invalid user a from 211.35.204.201
Jan 12 14:53:46 Sam-linux-server sshd[26835]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:46 Sam-linux-server sshd[26835]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:47 Sam-linux-server sshd[26835]: Failed password for invalid user a from 211.35.204.201 port 55489 ssh2
Jan 12 14:53:53 Sam-linux-server sshd[26837]: Invalid user a from 211.35.204.201
Jan 12 14:53:53 Sam-linux-server sshd[26837]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:53:53 Sam-linux-server sshd[26837]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:53:55 Sam-linux-server sshd[26837]: Failed password for invalid user a from 211.35.204.201 port 58653 ssh2
Jan 12 14:54:01 Sam-linux-server sshd[26839]: Invalid user a from 211.35.204.201
Jan 12 14:54:01 Sam-linux-server sshd[26839]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:01 Sam-linux-server sshd[26839]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:03 Sam-linux-server sshd[26839]: Failed password for invalid user a from 211.35.204.201 port 33630 ssh2
Jan 12 14:54:10 Sam-linux-server sshd[26841]: Invalid user a from 211.35.204.201
Jan 12 14:54:10 Sam-linux-server sshd[26841]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:10 Sam-linux-server sshd[26841]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:11 Sam-linux-server sshd[26841]: Failed password for invalid user a from 211.35.204.201 port 36976 ssh2
Jan 12 14:54:17 Sam-linux-server sshd[26844]: Invalid user a from 211.35.204.201
Jan 12 14:54:17 Sam-linux-server sshd[26844]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:17 Sam-linux-server sshd[26844]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:19 Sam-linux-server sshd[26844]: Failed password for invalid user a from 211.35.204.201 port 40199 ssh2
Jan 12 14:54:25 Sam-linux-server sshd[26846]: Invalid user a from 211.35.204.201
Jan 12 14:54:25 Sam-linux-server sshd[26846]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:25 Sam-linux-server sshd[26846]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:27 Sam-linux-server sshd[26846]: Failed password for invalid user a from 211.35.204.201 port 43418 ssh2
Jan 12 14:54:34 Sam-linux-server sshd[26848]: Invalid user a from 211.35.204.201
Jan 12 14:54:34 Sam-linux-server sshd[26848]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:34 Sam-linux-server sshd[26848]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:35 Sam-linux-server sshd[26848]: Failed password for invalid user a from 211.35.204.201 port 48028 ssh2
Jan 12 14:54:42 Sam-linux-server sshd[26850]: Invalid user a from 211.35.204.201
Jan 12 14:54:42 Sam-linux-server sshd[26850]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:42 Sam-linux-server sshd[26850]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:44 Sam-linux-server sshd[26850]: Failed password for invalid user a from 211.35.204.201 port 51393 ssh2
Jan 12 14:54:50 Sam-linux-server sshd[26852]: Invalid user a from 211.35.204.201
Jan 12 14:54:50 Sam-linux-server sshd[26852]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:50 Sam-linux-server sshd[26852]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:54:52 Sam-linux-server sshd[26852]: Failed password for invalid user a from 211.35.204.201 port 54766 ssh2
Jan 12 14:54:59 Sam-linux-server sshd[26854]: Invalid user a from 211.35.204.201
Jan 12 14:54:59 Sam-linux-server sshd[26854]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:54:59 Sam-linux-server sshd[26854]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:00 Sam-linux-server sshd[26854]: Failed password for invalid user a from 211.35.204.201 port 59831 ssh2
Jan 12 14:55:07 Sam-linux-server sshd[26856]: Invalid user a from 211.35.204.201
Jan 12 14:55:07 Sam-linux-server sshd[26856]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:07 Sam-linux-server sshd[26856]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:09 Sam-linux-server sshd[26856]: Failed password for invalid user a from 211.35.204.201 port 37114 ssh2
Jan 12 14:55:15 Sam-linux-server sshd[26858]: Invalid user a from 211.35.204.201
Jan 12 14:55:15 Sam-linux-server sshd[26858]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:15 Sam-linux-server sshd[26858]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:18 Sam-linux-server sshd[26858]: Failed password for invalid user a from 211.35.204.201 port 48138 ssh2
Jan 12 14:55:24 Sam-linux-server sshd[26860]: Invalid user a from 211.35.204.201
Jan 12 14:55:24 Sam-linux-server sshd[26860]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:24 Sam-linux-server sshd[26860]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:26 Sam-linux-server sshd[26860]: Failed password for invalid user a from 211.35.204.201 port 52635 ssh2
Jan 12 14:55:32 Sam-linux-server sshd[26862]: Invalid user a from 211.35.204.201
Jan 12 14:55:32 Sam-linux-server sshd[26862]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:32 Sam-linux-server sshd[26862]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:35 Sam-linux-server sshd[26862]: Failed password for invalid user a from 211.35.204.201 port 56018 ssh2
Jan 12 14:55:42 Sam-linux-server sshd[26864]: Invalid user a from 211.35.204.201
Jan 12 14:55:42 Sam-linux-server sshd[26864]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:42 Sam-linux-server sshd[26864]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:43 Sam-linux-server sshd[26864]: Failed password for invalid user a from 211.35.204.201 port 59324 ssh2
Jan 12 14:55:50 Sam-linux-server sshd[26866]: Invalid user a from 211.35.204.201
Jan 12 14:55:50 Sam-linux-server sshd[26866]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:50 Sam-linux-server sshd[26866]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:55:52 Sam-linux-server sshd[26866]: Failed password for invalid user a from 211.35.204.201 port 34807 ssh2
Jan 12 14:55:59 Sam-linux-server sshd[26868]: Invalid user a from 211.35.204.201
Jan 12 14:55:59 Sam-linux-server sshd[26868]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:55:59 Sam-linux-server sshd[26868]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:01 Sam-linux-server sshd[26868]: Failed password for invalid user a from 211.35.204.201 port 41167 ssh2
Jan 12 14:56:07 Sam-linux-server sshd[26870]: Invalid user a from 211.35.204.201
Jan 12 14:56:07 Sam-linux-server sshd[26870]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:07 Sam-linux-server sshd[26870]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:09 Sam-linux-server sshd[26870]: Failed password for invalid user a from 211.35.204.201 port 45302 ssh2
Jan 12 14:56:16 Sam-linux-server sshd[26872]: Invalid user a from 211.35.204.201
Jan 12 14:56:16 Sam-linux-server sshd[26872]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:16 Sam-linux-server sshd[26872]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:18 Sam-linux-server sshd[26872]: Failed password for invalid user a from 211.35.204.201 port 47179 ssh2
Jan 12 14:56:24 Sam-linux-server sshd[26874]: Invalid user b from 211.35.204.201
Jan 12 14:56:24 Sam-linux-server sshd[26874]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:24 Sam-linux-server sshd[26874]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:26 Sam-linux-server sshd[26874]: Failed password for invalid user b from 211.35.204.201 port 49065 ssh2
Jan 12 14:56:32 Sam-linux-server sshd[26876]: Invalid user b from 211.35.204.201
Jan 12 14:56:32 Sam-linux-server sshd[26876]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:32 Sam-linux-server sshd[26876]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:35 Sam-linux-server sshd[26876]: Failed password for invalid user b from 211.35.204.201 port 50873 ssh2
Jan 12 14:56:41 Sam-linux-server sshd[26878]: Invalid user b from 211.35.204.201
Jan 12 14:56:41 Sam-linux-server sshd[26878]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:41 Sam-linux-server sshd[26878]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:43 Sam-linux-server sshd[26878]: Failed password for invalid user b from 211.35.204.201 port 54833 ssh2
Jan 12 14:56:49 Sam-linux-server sshd[26880]: Invalid user b from 211.35.204.201
Jan 12 14:56:49 Sam-linux-server sshd[26880]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:49 Sam-linux-server sshd[26880]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:56:52 Sam-linux-server sshd[26880]: Failed password for invalid user b from 211.35.204.201 port 60745 ssh2
Jan 12 14:56:58 Sam-linux-server sshd[26882]: Invalid user b from 211.35.204.201
Jan 12 14:56:58 Sam-linux-server sshd[26882]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:56:58 Sam-linux-server sshd[26882]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:00 Sam-linux-server sshd[26882]: Failed password for invalid user b from 211.35.204.201 port 39074 ssh2
Jan 12 14:57:06 Sam-linux-server sshd[26884]: Invalid user b from 211.35.204.201
Jan 12 14:57:06 Sam-linux-server sshd[26884]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:06 Sam-linux-server sshd[26884]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:08 Sam-linux-server sshd[26884]: Failed password for invalid user b from 211.35.204.201 port 45500 ssh2
Jan 12 14:57:15 Sam-linux-server sshd[26886]: Invalid user b from 211.35.204.201
Jan 12 14:57:15 Sam-linux-server sshd[26886]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:15 Sam-linux-server sshd[26886]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:17 Sam-linux-server sshd[26886]: Failed password for invalid user b from 211.35.204.201 port 52396 ssh2
Jan 12 14:57:24 Sam-linux-server sshd[26888]: Invalid user b from 211.35.204.201
Jan 12 14:57:24 Sam-linux-server sshd[26888]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:24 Sam-linux-server sshd[26888]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:26 Sam-linux-server sshd[26888]: Failed password for invalid user b from 211.35.204.201 port 58638 ssh2
Jan 12 14:57:32 Sam-linux-server sshd[26890]: Invalid user b from 211.35.204.201
Jan 12 14:57:32 Sam-linux-server sshd[26890]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:32 Sam-linux-server sshd[26890]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:34 Sam-linux-server sshd[26890]: Failed password for invalid user b from 211.35.204.201 port 35994 ssh2
Jan 12 14:57:41 Sam-linux-server sshd[26892]: Invalid user b from 211.35.204.201
Jan 12 14:57:41 Sam-linux-server sshd[26892]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:41 Sam-linux-server sshd[26892]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:44 Sam-linux-server sshd[26892]: Failed password for invalid user b from 211.35.204.201 port 40929 ssh2
Jan 12 14:57:50 Sam-linux-server sshd[26894]: Invalid user b from 211.35.204.201
Jan 12 14:57:50 Sam-linux-server sshd[26894]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:50 Sam-linux-server sshd[26894]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:57:53 Sam-linux-server sshd[26894]: Failed password for invalid user b from 211.35.204.201 port 44567 ssh2
Jan 12 14:57:59 Sam-linux-server sshd[26896]: Invalid user b from 211.35.204.201
Jan 12 14:57:59 Sam-linux-server sshd[26896]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:57:59 Sam-linux-server sshd[26896]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:01 Sam-linux-server sshd[26896]: Failed password for invalid user b from 211.35.204.201 port 48203 ssh2
Jan 12 14:58:07 Sam-linux-server sshd[26898]: Invalid user b from 211.35.204.201
Jan 12 14:58:07 Sam-linux-server sshd[26898]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:07 Sam-linux-server sshd[26898]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:09 Sam-linux-server sshd[26898]: Failed password for invalid user b from 211.35.204.201 port 51426 ssh2
Jan 12 14:58:16 Sam-linux-server sshd[26900]: Invalid user b from 211.35.204.201
Jan 12 14:58:16 Sam-linux-server sshd[26900]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:16 Sam-linux-server sshd[26900]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:18 Sam-linux-server sshd[26900]: Failed password for invalid user b from 211.35.204.201 port 54844 ssh2
Jan 12 14:58:24 Sam-linux-server sshd[26902]: Invalid user b from 211.35.204.201
Jan 12 14:58:24 Sam-linux-server sshd[26902]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:24 Sam-linux-server sshd[26902]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:26 Sam-linux-server sshd[26902]: Failed password for invalid user b from 211.35.204.201 port 33198 ssh2
Jan 12 14:58:33 Sam-linux-server sshd[26904]: Invalid user b from 211.35.204.201
Jan 12 14:58:33 Sam-linux-server sshd[26904]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:33 Sam-linux-server sshd[26904]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:35 Sam-linux-server sshd[26904]: Failed password for invalid user b from 211.35.204.201 port 36789 ssh2
Jan 12 14:58:41 Sam-linux-server sshd[26906]: Invalid user b from 211.35.204.201
Jan 12 14:58:41 Sam-linux-server sshd[26906]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:41 Sam-linux-server sshd[26906]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:43 Sam-linux-server sshd[26906]: Failed password for invalid user b from 211.35.204.201 port 40936 ssh2
Jan 12 14:58:50 Sam-linux-server sshd[26908]: Invalid user b from 211.35.204.201
Jan 12 14:58:50 Sam-linux-server sshd[26908]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:50 Sam-linux-server sshd[26908]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:58:52 Sam-linux-server sshd[26908]: Failed password for invalid user b from 211.35.204.201 port 48468 ssh2
Jan 12 14:58:58 Sam-linux-server sshd[26910]: Invalid user b from 211.35.204.201
Jan 12 14:58:58 Sam-linux-server sshd[26910]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:58:58 Sam-linux-server sshd[26910]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:00 Sam-linux-server sshd[26910]: Failed password for invalid user b from 211.35.204.201 port 56489 ssh2
Jan 12 14:59:06 Sam-linux-server sshd[26912]: Invalid user b from 211.35.204.201
Jan 12 14:59:06 Sam-linux-server sshd[26912]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:06 Sam-linux-server sshd[26912]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:08 Sam-linux-server sshd[26912]: Failed password for invalid user b from 211.35.204.201 port 60527 ssh2
Jan 12 14:59:15 Sam-linux-server sshd[26914]: Invalid user b from 211.35.204.201
Jan 12 14:59:15 Sam-linux-server sshd[26914]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:15 Sam-linux-server sshd[26914]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:17 Sam-linux-server sshd[26914]: Failed password for invalid user b from 211.35.204.201 port 34013 ssh2
Jan 12 14:59:24 Sam-linux-server sshd[26916]: Invalid user b from 211.35.204.201
Jan 12 14:59:24 Sam-linux-server sshd[26916]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:24 Sam-linux-server sshd[26916]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:26 Sam-linux-server sshd[26916]: Failed password for invalid user b from 211.35.204.201 port 35771 ssh2
Jan 12 14:59:32 Sam-linux-server sshd[26918]: Invalid user b from 211.35.204.201
Jan 12 14:59:32 Sam-linux-server sshd[26918]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:32 Sam-linux-server sshd[26918]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:34 Sam-linux-server sshd[26918]: Failed password for invalid user b from 211.35.204.201 port 39513 ssh2
Jan 12 14:59:40 Sam-linux-server sshd[26920]: Invalid user b from 211.35.204.201
Jan 12 14:59:40 Sam-linux-server sshd[26920]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:40 Sam-linux-server sshd[26920]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:42 Sam-linux-server sshd[26920]: Failed password for invalid user b from 211.35.204.201 port 42688 ssh2
Jan 12 14:59:48 Sam-linux-server sshd[26922]: Invalid user b from 211.35.204.201
Jan 12 14:59:48 Sam-linux-server sshd[26922]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:48 Sam-linux-server sshd[26922]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:51 Sam-linux-server sshd[26922]: Failed password for invalid user b from 211.35.204.201 port 45857 ssh2
Jan 12 14:59:57 Sam-linux-server sshd[26924]: Invalid user b from 211.35.204.201
Jan 12 14:59:57 Sam-linux-server sshd[26924]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 14:59:57 Sam-linux-server sshd[26924]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 14:59:59 Sam-linux-server sshd[26924]: Failed password for invalid user b from 211.35.204.201 port 50084 ssh2
Jan 12 15:00:06 Sam-linux-server sshd[26926]: Invalid user c from 211.35.204.201
Jan 12 15:00:06 Sam-linux-server sshd[26926]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:06 Sam-linux-server sshd[26926]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:07 Sam-linux-server sshd[26926]: Failed password for invalid user c from 211.35.204.201 port 53613 ssh2
Jan 12 15:00:14 Sam-linux-server sshd[26928]: Invalid user c from 211.35.204.201
Jan 12 15:00:14 Sam-linux-server sshd[26928]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:14 Sam-linux-server sshd[26928]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:15 Sam-linux-server sshd[26928]: Failed password for invalid user c from 211.35.204.201 port 33533 ssh2
Jan 12 15:00:22 Sam-linux-server sshd[26930]: Invalid user c from 211.35.204.201
Jan 12 15:00:22 Sam-linux-server sshd[26930]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:22 Sam-linux-server sshd[26930]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:24 Sam-linux-server sshd[26930]: Failed password for invalid user c from 211.35.204.201 port 40408 ssh2
Jan 12 15:00:30 Sam-linux-server sshd[26932]: Invalid user c from 211.35.204.201
Jan 12 15:00:30 Sam-linux-server sshd[26932]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:30 Sam-linux-server sshd[26932]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:32 Sam-linux-server sshd[26932]: Failed password for invalid user c from 211.35.204.201 port 46366 ssh2
Jan 12 15:00:38 Sam-linux-server sshd[26934]: Invalid user c from 211.35.204.201
Jan 12 15:00:38 Sam-linux-server sshd[26934]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:38 Sam-linux-server sshd[26934]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:40 Sam-linux-server sshd[26934]: Failed password for invalid user c from 211.35.204.201 port 49573 ssh2
Jan 12 15:00:47 Sam-linux-server sshd[26936]: Invalid user c from 211.35.204.201
Jan 12 15:00:47 Sam-linux-server sshd[26936]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:47 Sam-linux-server sshd[26936]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:49 Sam-linux-server sshd[26936]: Failed password for invalid user c from 211.35.204.201 port 52868 ssh2
Jan 12 15:00:56 Sam-linux-server sshd[26938]: Invalid user c from 211.35.204.201
Jan 12 15:00:56 Sam-linux-server sshd[26938]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:00:56 Sam-linux-server sshd[26938]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:00:58 Sam-linux-server sshd[26938]: Failed password for invalid user c from 211.35.204.201 port 56212 ssh2
Jan 12 15:01:04 Sam-linux-server sshd[26940]: Invalid user c from 211.35.204.201
Jan 12 15:01:04 Sam-linux-server sshd[26940]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:04 Sam-linux-server sshd[26940]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:05 Sam-linux-server sshd[26940]: Failed password for invalid user c from 211.35.204.201 port 59684 ssh2
Jan 12 15:01:12 Sam-linux-server sshd[26942]: Invalid user c from 211.35.204.201
Jan 12 15:01:12 Sam-linux-server sshd[26942]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:12 Sam-linux-server sshd[26942]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:13 Sam-linux-server sshd[26942]: Failed password for invalid user c from 211.35.204.201 port 34306 ssh2
Jan 12 15:01:20 Sam-linux-server sshd[26944]: Invalid user c from 211.35.204.201
Jan 12 15:01:20 Sam-linux-server sshd[26944]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:20 Sam-linux-server sshd[26944]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:22 Sam-linux-server sshd[26944]: Failed password for invalid user c from 211.35.204.201 port 37776 ssh2
Jan 12 15:01:29 Sam-linux-server sshd[26946]: Invalid user c from 211.35.204.201
Jan 12 15:01:29 Sam-linux-server sshd[26946]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:29 Sam-linux-server sshd[26946]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:31 Sam-linux-server sshd[26946]: Failed password for invalid user c from 211.35.204.201 port 41059 ssh2
Jan 12 15:01:37 Sam-linux-server sshd[26948]: Invalid user c from 211.35.204.201
Jan 12 15:01:37 Sam-linux-server sshd[26948]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:37 Sam-linux-server sshd[26948]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:39 Sam-linux-server sshd[26948]: Failed password for invalid user c from 211.35.204.201 port 44536 ssh2
Jan 12 15:01:46 Sam-linux-server sshd[26950]: Invalid user c from 211.35.204.201
Jan 12 15:01:46 Sam-linux-server sshd[26950]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:46 Sam-linux-server sshd[26950]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:47 Sam-linux-server sshd[26950]: Failed password for invalid user c from 211.35.204.201 port 47959 ssh2
Jan 12 15:01:54 Sam-linux-server sshd[26952]: Invalid user c from 211.35.204.201
Jan 12 15:01:54 Sam-linux-server sshd[26952]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:01:54 Sam-linux-server sshd[26952]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:01:56 Sam-linux-server sshd[26952]: Failed password for invalid user c from 211.35.204.201 port 55691 ssh2
Jan 12 15:02:02 Sam-linux-server sshd[26954]: Invalid user c from 211.35.204.201
Jan 12 15:02:02 Sam-linux-server sshd[26954]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:02 Sam-linux-server sshd[26954]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:04 Sam-linux-server sshd[26954]: Failed password for invalid user c from 211.35.204.201 port 59605 ssh2
Jan 12 15:02:11 Sam-linux-server sshd[26956]: Invalid user c from 211.35.204.201
Jan 12 15:02:11 Sam-linux-server sshd[26956]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:11 Sam-linux-server sshd[26956]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:13 Sam-linux-server sshd[26956]: Failed password for invalid user c from 211.35.204.201 port 34631 ssh2
Jan 12 15:02:19 Sam-linux-server sshd[26958]: Invalid user c from 211.35.204.201
Jan 12 15:02:19 Sam-linux-server sshd[26958]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:19 Sam-linux-server sshd[26958]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:21 Sam-linux-server sshd[26958]: Failed password for invalid user c from 211.35.204.201 port 38000 ssh2
Jan 12 15:02:28 Sam-linux-server sshd[26960]: Invalid user c from 211.35.204.201
Jan 12 15:02:28 Sam-linux-server sshd[26960]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:28 Sam-linux-server sshd[26960]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:29 Sam-linux-server sshd[26960]: Failed password for invalid user c from 211.35.204.201 port 41205 ssh2
Jan 12 15:02:36 Sam-linux-server sshd[26962]: Invalid user c from 211.35.204.201
Jan 12 15:02:36 Sam-linux-server sshd[26962]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:36 Sam-linux-server sshd[26962]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:38 Sam-linux-server sshd[26962]: Failed password for invalid user c from 211.35.204.201 port 44441 ssh2
Jan 12 15:02:44 Sam-linux-server sshd[26964]: Invalid user c from 211.35.204.201
Jan 12 15:02:44 Sam-linux-server sshd[26964]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:44 Sam-linux-server sshd[26964]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:46 Sam-linux-server sshd[26964]: Failed password for invalid user c from 211.35.204.201 port 47644 ssh2
Jan 12 15:02:52 Sam-linux-server sshd[26966]: Invalid user c from 211.35.204.201
Jan 12 15:02:52 Sam-linux-server sshd[26966]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:02:52 Sam-linux-server sshd[26966]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:02:55 Sam-linux-server sshd[26966]: Failed password for invalid user c from 211.35.204.201 port 50857 ssh2
Jan 12 15:03:01 Sam-linux-server sshd[26968]: Invalid user c from 211.35.204.201
Jan 12 15:03:01 Sam-linux-server sshd[26968]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:01 Sam-linux-server sshd[26968]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:04 Sam-linux-server sshd[26968]: Failed password for invalid user c from 211.35.204.201 port 54204 ssh2
Jan 12 15:03:10 Sam-linux-server sshd[26970]: Invalid user c from 211.35.204.201
Jan 12 15:03:10 Sam-linux-server sshd[26970]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:10 Sam-linux-server sshd[26970]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:12 Sam-linux-server sshd[26970]: Failed password for invalid user c from 211.35.204.201 port 58109 ssh2
Jan 12 15:03:18 Sam-linux-server sshd[26972]: Invalid user c from 211.35.204.201
Jan 12 15:03:18 Sam-linux-server sshd[26972]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:18 Sam-linux-server sshd[26972]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:20 Sam-linux-server sshd[26972]: Failed password for invalid user c from 211.35.204.201 port 33073 ssh2
Jan 12 15:03:27 Sam-linux-server sshd[26974]: Invalid user c from 211.35.204.201
Jan 12 15:03:27 Sam-linux-server sshd[26974]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:27 Sam-linux-server sshd[26974]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:29 Sam-linux-server sshd[26974]: Failed password for invalid user c from 211.35.204.201 port 35079 ssh2
Jan 12 15:03:36 Sam-linux-server sshd[26976]: Invalid user c from 211.35.204.201
Jan 12 15:03:36 Sam-linux-server sshd[26976]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:36 Sam-linux-server sshd[26976]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:38 Sam-linux-server sshd[26976]: Failed password for invalid user c from 211.35.204.201 port 37026 ssh2
Jan 12 15:03:44 Sam-linux-server sshd[26978]: Invalid user d from 211.35.204.201
Jan 12 15:03:44 Sam-linux-server sshd[26978]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:44 Sam-linux-server sshd[26978]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:47 Sam-linux-server sshd[26978]: Failed password for invalid user d from 211.35.204.201 port 38932 ssh2
Jan 12 15:03:53 Sam-linux-server sshd[26980]: Invalid user d from 211.35.204.201
Jan 12 15:03:53 Sam-linux-server sshd[26980]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:03:53 Sam-linux-server sshd[26980]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:03:55 Sam-linux-server sshd[26980]: Failed password for invalid user d from 211.35.204.201 port 40893 ssh2
Jan 12 15:04:02 Sam-linux-server sshd[26982]: Invalid user d from 211.35.204.201
Jan 12 15:04:02 Sam-linux-server sshd[26982]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:02 Sam-linux-server sshd[26982]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:05 Sam-linux-server sshd[26982]: Failed password for invalid user d from 211.35.204.201 port 44363 ssh2
Jan 12 15:04:12 Sam-linux-server sshd[26984]: Invalid user d from 211.35.204.201
Jan 12 15:04:12 Sam-linux-server sshd[26984]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:12 Sam-linux-server sshd[26984]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:14 Sam-linux-server sshd[26984]: Failed password for invalid user d from 211.35.204.201 port 47948 ssh2
Jan 12 15:04:20 Sam-linux-server sshd[26986]: Invalid user d from 211.35.204.201
Jan 12 15:04:20 Sam-linux-server sshd[26986]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:20 Sam-linux-server sshd[26986]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:22 Sam-linux-server sshd[26986]: Failed password for invalid user d from 211.35.204.201 port 51432 ssh2
Jan 12 15:04:29 Sam-linux-server sshd[26988]: Invalid user d from 211.35.204.201
Jan 12 15:04:29 Sam-linux-server sshd[26988]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:29 Sam-linux-server sshd[26988]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:31 Sam-linux-server sshd[26988]: Failed password for invalid user d from 211.35.204.201 port 54846 ssh2
Jan 12 15:04:37 Sam-linux-server sshd[26990]: Invalid user d from 211.35.204.201
Jan 12 15:04:37 Sam-linux-server sshd[26990]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:37 Sam-linux-server sshd[26990]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:39 Sam-linux-server sshd[26990]: Failed password for invalid user d from 211.35.204.201 port 39240 ssh2
Jan 12 15:04:46 Sam-linux-server sshd[26992]: Invalid user d from 211.35.204.201
Jan 12 15:04:46 Sam-linux-server sshd[26992]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:46 Sam-linux-server sshd[26992]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:48 Sam-linux-server sshd[26992]: Failed password for invalid user d from 211.35.204.201 port 42577 ssh2
Jan 12 15:04:55 Sam-linux-server sshd[26994]: Invalid user d from 211.35.204.201
Jan 12 15:04:55 Sam-linux-server sshd[26994]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:04:55 Sam-linux-server sshd[26994]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:04:56 Sam-linux-server sshd[26994]: Failed password for invalid user d from 211.35.204.201 port 46024 ssh2
Jan 12 15:05:03 Sam-linux-server sshd[26996]: Invalid user d from 211.35.204.201
Jan 12 15:05:03 Sam-linux-server sshd[26996]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:03 Sam-linux-server sshd[26996]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:05 Sam-linux-server sshd[26996]: Failed password for invalid user d from 211.35.204.201 port 49400 ssh2
Jan 12 15:05:12 Sam-linux-server sshd[26998]: Invalid user d from 211.35.204.201
Jan 12 15:05:12 Sam-linux-server sshd[26998]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:12 Sam-linux-server sshd[26998]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:13 Sam-linux-server sshd[26998]: Failed password for invalid user d from 211.35.204.201 port 52901 ssh2
Jan 12 15:05:20 Sam-linux-server sshd[27000]: Invalid user d from 211.35.204.201
Jan 12 15:05:20 Sam-linux-server sshd[27000]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:20 Sam-linux-server sshd[27000]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:22 Sam-linux-server sshd[27000]: Failed password for invalid user d from 211.35.204.201 port 56200 ssh2
Jan 12 15:05:28 Sam-linux-server sshd[27002]: Invalid user d from 211.35.204.201
Jan 12 15:05:28 Sam-linux-server sshd[27002]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:28 Sam-linux-server sshd[27002]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:31 Sam-linux-server sshd[27002]: Failed password for invalid user d from 211.35.204.201 port 59553 ssh2
Jan 12 15:05:38 Sam-linux-server sshd[27004]: Invalid user d from 211.35.204.201
Jan 12 15:05:38 Sam-linux-server sshd[27004]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:38 Sam-linux-server sshd[27004]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:40 Sam-linux-server sshd[27004]: Failed password for invalid user d from 211.35.204.201 port 35619 ssh2
Jan 12 15:05:46 Sam-linux-server sshd[27006]: Invalid user d from 211.35.204.201
Jan 12 15:05:46 Sam-linux-server sshd[27006]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:46 Sam-linux-server sshd[27006]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:48 Sam-linux-server sshd[27006]: Failed password for invalid user d from 211.35.204.201 port 39019 ssh2
Jan 12 15:05:55 Sam-linux-server sshd[27008]: Invalid user d from 211.35.204.201
Jan 12 15:05:55 Sam-linux-server sshd[27008]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:05:55 Sam-linux-server sshd[27008]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:05:57 Sam-linux-server sshd[27008]: Failed password for invalid user d from 211.35.204.201 port 42440 ssh2
Jan 12 15:06:03 Sam-linux-server sshd[27010]: Invalid user d from 211.35.204.201
Jan 12 15:06:03 Sam-linux-server sshd[27010]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:03 Sam-linux-server sshd[27010]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:06 Sam-linux-server sshd[27010]: Failed password for invalid user d from 211.35.204.201 port 45762 ssh2
Jan 12 15:06:12 Sam-linux-server sshd[27012]: Invalid user d from 211.35.204.201
Jan 12 15:06:12 Sam-linux-server sshd[27012]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:12 Sam-linux-server sshd[27012]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:14 Sam-linux-server sshd[27012]: Failed password for invalid user d from 211.35.204.201 port 49260 ssh2
Jan 12 15:06:21 Sam-linux-server sshd[27014]: Invalid user d from 211.35.204.201
Jan 12 15:06:21 Sam-linux-server sshd[27014]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:21 Sam-linux-server sshd[27014]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:23 Sam-linux-server sshd[27014]: Failed password for invalid user d from 211.35.204.201 port 52590 ssh2
Jan 12 15:06:29 Sam-linux-server sshd[27016]: Invalid user d from 211.35.204.201
Jan 12 15:06:29 Sam-linux-server sshd[27016]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:29 Sam-linux-server sshd[27016]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:31 Sam-linux-server sshd[27016]: Failed password for invalid user d from 211.35.204.201 port 56740 ssh2
Jan 12 15:06:37 Sam-linux-server sshd[27018]: Invalid user d from 211.35.204.201
Jan 12 15:06:37 Sam-linux-server sshd[27018]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:37 Sam-linux-server sshd[27018]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:40 Sam-linux-server sshd[27018]: Failed password for invalid user d from 211.35.204.201 port 60101 ssh2
Jan 12 15:06:47 Sam-linux-server sshd[27020]: Invalid user d from 211.35.204.201
Jan 12 15:06:47 Sam-linux-server sshd[27020]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:47 Sam-linux-server sshd[27020]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:48 Sam-linux-server sshd[27020]: Failed password for invalid user d from 211.35.204.201 port 35330 ssh2
Jan 12 15:06:55 Sam-linux-server sshd[27022]: Invalid user d from 211.35.204.201
Jan 12 15:06:55 Sam-linux-server sshd[27022]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:06:55 Sam-linux-server sshd[27022]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:06:57 Sam-linux-server sshd[27022]: Failed password for invalid user d from 211.35.204.201 port 38711 ssh2
Jan 12 15:07:03 Sam-linux-server sshd[27024]: Invalid user d from 211.35.204.201
Jan 12 15:07:03 Sam-linux-server sshd[27024]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:03 Sam-linux-server sshd[27024]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:05 Sam-linux-server sshd[27024]: Failed password for invalid user d from 211.35.204.201 port 42078 ssh2
Jan 12 15:07:12 Sam-linux-server sshd[27026]: Invalid user d from 211.35.204.201
Jan 12 15:07:12 Sam-linux-server sshd[27026]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:12 Sam-linux-server sshd[27026]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:13 Sam-linux-server sshd[27026]: Failed password for invalid user d from 211.35.204.201 port 45464 ssh2
Jan 12 15:07:20 Sam-linux-server sshd[27028]: Invalid user d from 211.35.204.201
Jan 12 15:07:20 Sam-linux-server sshd[27028]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:20 Sam-linux-server sshd[27028]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:22 Sam-linux-server sshd[27028]: Failed password for invalid user d from 211.35.204.201 port 48736 ssh2
Jan 12 15:07:28 Sam-linux-server sshd[27030]: Invalid user e from 211.35.204.201
Jan 12 15:07:28 Sam-linux-server sshd[27030]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:28 Sam-linux-server sshd[27030]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:30 Sam-linux-server sshd[27030]: Failed password for invalid user e from 211.35.204.201 port 51997 ssh2
Jan 12 15:07:37 Sam-linux-server sshd[27032]: Invalid user e from 211.35.204.201
Jan 12 15:07:37 Sam-linux-server sshd[27032]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:37 Sam-linux-server sshd[27032]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:39 Sam-linux-server sshd[27032]: Failed password for invalid user e from 211.35.204.201 port 55343 ssh2
Jan 12 15:07:45 Sam-linux-server sshd[27034]: Invalid user e from 211.35.204.201
Jan 12 15:07:45 Sam-linux-server sshd[27034]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:45 Sam-linux-server sshd[27034]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:47 Sam-linux-server sshd[27034]: Failed password for invalid user e from 211.35.204.201 port 59468 ssh2
Jan 12 15:07:54 Sam-linux-server sshd[27036]: Invalid user e from 211.35.204.201
Jan 12 15:07:54 Sam-linux-server sshd[27036]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:07:54 Sam-linux-server sshd[27036]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:07:56 Sam-linux-server sshd[27036]: Failed password for invalid user e from 211.35.204.201 port 34559 ssh2
Jan 12 15:08:02 Sam-linux-server sshd[27038]: Invalid user e from 211.35.204.201
Jan 12 15:08:02 Sam-linux-server sshd[27038]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:02 Sam-linux-server sshd[27038]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:04 Sam-linux-server sshd[27038]: Failed password for invalid user e from 211.35.204.201 port 37845 ssh2
Jan 12 15:08:10 Sam-linux-server sshd[27040]: Invalid user e from 211.35.204.201
Jan 12 15:08:10 Sam-linux-server sshd[27040]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:10 Sam-linux-server sshd[27040]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:13 Sam-linux-server sshd[27040]: Failed password for invalid user e from 211.35.204.201 port 41185 ssh2
Jan 12 15:08:19 Sam-linux-server sshd[27042]: Invalid user e from 211.35.204.201
Jan 12 15:08:19 Sam-linux-server sshd[27042]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:19 Sam-linux-server sshd[27042]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:22 Sam-linux-server sshd[27042]: Failed password for invalid user e from 211.35.204.201 port 44560 ssh2
Jan 12 15:08:28 Sam-linux-server sshd[27044]: Invalid user e from 211.35.204.201
Jan 12 15:08:28 Sam-linux-server sshd[27044]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:28 Sam-linux-server sshd[27044]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:30 Sam-linux-server sshd[27044]: Failed password for invalid user e from 211.35.204.201 port 47981 ssh2
Jan 12 15:08:37 Sam-linux-server sshd[27046]: Invalid user e from 211.35.204.201
Jan 12 15:08:37 Sam-linux-server sshd[27046]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:37 Sam-linux-server sshd[27046]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:39 Sam-linux-server sshd[27046]: Failed password for invalid user e from 211.35.204.201 port 52022 ssh2
Jan 12 15:08:45 Sam-linux-server sshd[27048]: Invalid user e from 211.35.204.201
Jan 12 15:08:45 Sam-linux-server sshd[27048]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:45 Sam-linux-server sshd[27048]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:47 Sam-linux-server sshd[27048]: Failed password for invalid user e from 211.35.204.201 port 55425 ssh2
Jan 12 15:08:54 Sam-linux-server sshd[27050]: Invalid user e from 211.35.204.201
Jan 12 15:08:54 Sam-linux-server sshd[27050]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:08:54 Sam-linux-server sshd[27050]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:08:56 Sam-linux-server sshd[27050]: Failed password for invalid user e from 211.35.204.201 port 58766 ssh2
Jan 12 15:09:02 Sam-linux-server sshd[27052]: Invalid user e from 211.35.204.201
Jan 12 15:09:02 Sam-linux-server sshd[27052]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:02 Sam-linux-server sshd[27052]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:05 Sam-linux-server sshd[27052]: Failed password for invalid user e from 211.35.204.201 port 33847 ssh2
Jan 12 15:09:11 Sam-linux-server sshd[27054]: Invalid user e from 211.35.204.201
Jan 12 15:09:11 Sam-linux-server sshd[27054]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:11 Sam-linux-server sshd[27054]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:13 Sam-linux-server sshd[27054]: Failed password for invalid user e from 211.35.204.201 port 37248 ssh2
Jan 12 15:09:20 Sam-linux-server sshd[27056]: Invalid user e from 211.35.204.201
Jan 12 15:09:20 Sam-linux-server sshd[27056]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:20 Sam-linux-server sshd[27056]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:22 Sam-linux-server sshd[27056]: Failed password for invalid user e from 211.35.204.201 port 39125 ssh2
Jan 12 15:09:28 Sam-linux-server sshd[27058]: Invalid user e from 211.35.204.201
Jan 12 15:09:28 Sam-linux-server sshd[27058]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:28 Sam-linux-server sshd[27058]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:30 Sam-linux-server sshd[27058]: Failed password for invalid user e from 211.35.204.201 port 40977 ssh2
Jan 12 15:09:37 Sam-linux-server sshd[27060]: Invalid user e from 211.35.204.201
Jan 12 15:09:37 Sam-linux-server sshd[27060]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:37 Sam-linux-server sshd[27060]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:39 Sam-linux-server sshd[27060]: Failed password for invalid user e from 211.35.204.201 port 60665 ssh2
Jan 12 15:09:46 Sam-linux-server sshd[27062]: Invalid user e from 211.35.204.201
Jan 12 15:09:46 Sam-linux-server sshd[27062]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:46 Sam-linux-server sshd[27062]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:48 Sam-linux-server sshd[27062]: Failed password for invalid user e from 211.35.204.201 port 36065 ssh2
Jan 12 15:09:55 Sam-linux-server sshd[27064]: Invalid user e from 211.35.204.201
Jan 12 15:09:55 Sam-linux-server sshd[27064]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:09:55 Sam-linux-server sshd[27064]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:09:57 Sam-linux-server sshd[27064]: Failed password for invalid user e from 211.35.204.201 port 39564 ssh2
Jan 12 15:10:03 Sam-linux-server sshd[27066]: Invalid user e from 211.35.204.201
Jan 12 15:10:03 Sam-linux-server sshd[27066]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:03 Sam-linux-server sshd[27066]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:06 Sam-linux-server sshd[27066]: Failed password for invalid user e from 211.35.204.201 port 42956 ssh2
Jan 12 15:10:12 Sam-linux-server sshd[27068]: Invalid user e from 211.35.204.201
Jan 12 15:10:12 Sam-linux-server sshd[27068]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:12 Sam-linux-server sshd[27068]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:14 Sam-linux-server sshd[27068]: Failed password for invalid user e from 211.35.204.201 port 47357 ssh2
Jan 12 15:10:21 Sam-linux-server sshd[27070]: Invalid user e from 211.35.204.201
Jan 12 15:10:21 Sam-linux-server sshd[27070]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:21 Sam-linux-server sshd[27070]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:23 Sam-linux-server sshd[27070]: Failed password for invalid user e from 211.35.204.201 port 50817 ssh2
Jan 12 15:10:30 Sam-linux-server sshd[27072]: Invalid user e from 211.35.204.201
Jan 12 15:10:30 Sam-linux-server sshd[27072]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:30 Sam-linux-server sshd[27072]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:32 Sam-linux-server sshd[27072]: Failed password for invalid user e from 211.35.204.201 port 54298 ssh2
Jan 12 15:10:38 Sam-linux-server sshd[27074]: Invalid user e from 211.35.204.201
Jan 12 15:10:38 Sam-linux-server sshd[27074]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:38 Sam-linux-server sshd[27074]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:40 Sam-linux-server sshd[27074]: Failed password for invalid user e from 211.35.204.201 port 57658 ssh2
Jan 12 15:10:47 Sam-linux-server sshd[27076]: Invalid user e from 211.35.204.201
Jan 12 15:10:47 Sam-linux-server sshd[27076]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:47 Sam-linux-server sshd[27076]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:49 Sam-linux-server sshd[27076]: Failed password for invalid user e from 211.35.204.201 port 32906 ssh2
Jan 12 15:10:55 Sam-linux-server sshd[27078]: Invalid user e from 211.35.204.201
Jan 12 15:10:55 Sam-linux-server sshd[27078]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:10:55 Sam-linux-server sshd[27078]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:10:57 Sam-linux-server sshd[27078]: Failed password for invalid user e from 211.35.204.201 port 36334 ssh2
Jan 12 15:11:04 Sam-linux-server sshd[27080]: Invalid user e from 211.35.204.201
Jan 12 15:11:04 Sam-linux-server sshd[27080]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:04 Sam-linux-server sshd[27080]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:06 Sam-linux-server sshd[27080]: Failed password for invalid user e from 211.35.204.201 port 40564 ssh2
Jan 12 15:11:13 Sam-linux-server sshd[27082]: Invalid user f from 211.35.204.201
Jan 12 15:11:13 Sam-linux-server sshd[27082]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:13 Sam-linux-server sshd[27082]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:15 Sam-linux-server sshd[27082]: Failed password for invalid user f from 211.35.204.201 port 44144 ssh2
Jan 12 15:11:21 Sam-linux-server sshd[27084]: Invalid user f from 211.35.204.201
Jan 12 15:11:21 Sam-linux-server sshd[27084]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:21 Sam-linux-server sshd[27084]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:24 Sam-linux-server sshd[27084]: Failed password for invalid user f from 211.35.204.201 port 47412 ssh2
Jan 12 15:11:30 Sam-linux-server sshd[27086]: Invalid user f from 211.35.204.201
Jan 12 15:11:30 Sam-linux-server sshd[27086]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:30 Sam-linux-server sshd[27086]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:32 Sam-linux-server sshd[27086]: Failed password for invalid user f from 211.35.204.201 port 50949 ssh2
Jan 12 15:11:39 Sam-linux-server sshd[27088]: Invalid user f from 211.35.204.201
Jan 12 15:11:39 Sam-linux-server sshd[27088]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:39 Sam-linux-server sshd[27088]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:41 Sam-linux-server sshd[27088]: Failed password for invalid user f from 211.35.204.201 port 54360 ssh2
Jan 12 15:11:47 Sam-linux-server sshd[27090]: Invalid user f from 211.35.204.201
Jan 12 15:11:47 Sam-linux-server sshd[27090]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:47 Sam-linux-server sshd[27090]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:49 Sam-linux-server sshd[27090]: Failed password for invalid user f from 211.35.204.201 port 57737 ssh2
Jan 12 15:11:55 Sam-linux-server sshd[27092]: Invalid user f from 211.35.204.201
Jan 12 15:11:55 Sam-linux-server sshd[27092]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:11:55 Sam-linux-server sshd[27092]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:11:57 Sam-linux-server sshd[27092]: Failed password for invalid user f from 211.35.204.201 port 32774 ssh2
Jan 12 15:12:04 Sam-linux-server sshd[27094]: Invalid user f from 211.35.204.201
Jan 12 15:12:04 Sam-linux-server sshd[27094]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:12:04 Sam-linux-server sshd[27094]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:12:06 Sam-linux-server sshd[27094]: Failed password for invalid user f from 211.35.204.201 port 36083 ssh2
Jan 12 15:12:13 Sam-linux-server sshd[27096]: Invalid user f from 211.35.204.201
Jan 12 15:12:13 Sam-linux-server sshd[27096]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:12:13 Sam-linux-server sshd[27096]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:12:14 Sam-linux-server sshd[27096]: Failed password for invalid user f from 211.35.204.201 port 44868 ssh2
Jan 12 15:12:21 Sam-linux-server sshd[27098]: Invalid user f from 211.35.204.201
Jan 12 15:12:21 Sam-linux-server sshd[27098]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:12:21 Sam-linux-server sshd[27098]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:12:23 Sam-linux-server sshd[27098]: Failed password for invalid user f from 211.35.204.201 port 50457 ssh2
Jan 12 15:12:29 Sam-linux-server sshd[27100]: Invalid user f from 211.35.204.201
Jan 12 15:12:29 Sam-linux-server sshd[27100]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:12:29 Sam-linux-server sshd[27100]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:12:31 Sam-linux-server sshd[27100]: Failed password for invalid user f from 211.35.204.201 port 58465 ssh2
Jan 12 15:12:41 Sam-linux-server sshd[27102]: Invalid user f from 211.35.204.201
Jan 12 15:12:41 Sam-linux-server sshd[27102]: pam_unix(sshd:auth): check pass; user unknown
Jan 12 15:12:41 Sam-linux-server sshd[27102]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=211.35.204.201 
Jan 12 15:12:43 Sam-linux-server sshd[27102]: Failed password for invalid user f from 211.35.204.201 port 33647 ssh2
Jan 12 15:17:01 Sam-linux-server CRON[27105]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 15:17:01 Sam-linux-server CRON[27105]: pam_unix(cron:session): session closed for user root
Jan 12 15:17:28 Sam-linux-server sshd[27108]: Accepted password for root from 72.193.243.114 port 50047 ssh2
Jan 12 15:17:28 Sam-linux-server sshd[27108]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 15:17:28 Sam-linux-server sshd[27108]: subsystem request for sftp
Jan 12 15:19:41 Sam-linux-server sshd[27163]: Accepted password for root from 72.193.243.114 port 50070 ssh2
Jan 12 15:19:41 Sam-linux-server sshd[27163]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 15:19:41 Sam-linux-server sshd[27163]: subsystem request for sftp
Jan 12 15:32:52 Sam-linux-server sshd[27221]: Accepted password for root from 72.193.243.114 port 50073 ssh2
Jan 12 15:32:52 Sam-linux-server sshd[27221]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 15:39:03 Sam-linux-server sshd[27221]: pam_unix(sshd:session): session closed for user root
Jan 12 15:40:16 Sam-linux-server sshd[27108]: pam_unix(sshd:session): session closed for user root
Jan 12 15:40:16 Sam-linux-server sshd[27163]: pam_unix(sshd:session): session closed for user root
Jan 12 15:42:42 Sam-linux-server sshd[27376]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ip72-193-243-114.lv.lv.cox.net  user=sam
Jan 12 15:42:44 Sam-linux-server sshd[27376]: Failed password for sam from 72.193.243.114 port 50077 ssh2
Jan 12 15:42:46 Sam-linux-server sshd[27376]: Accepted password for sam from 72.193.243.114 port 50077 ssh2
Jan 12 15:42:47 Sam-linux-server sshd[27376]: pam_unix(sshd:session): session opened for user sam by (uid=0)
Jan 12 15:45:21 Sam-linux-server su[27496]: Successful su for root by sam
Jan 12 15:45:21 Sam-linux-server su[27496]: + /dev/pts/0 sam:root
Jan 12 15:45:21 Sam-linux-server su[27496]: pam_unix(su:session): session opened for user root by sam(uid=1000)
Jan 12 15:50:14 Sam-linux-server su[27496]: pam_unix(su:session): session closed for user root
Jan 12 15:50:18 Sam-linux-server sshd[27376]: pam_unix(sshd:session): session closed for user sam
Jan 12 15:55:06 Sam-linux-server sshd[988]: Server listening on 0.0.0.0 port 22.
Jan 12 15:55:06 Sam-linux-server sshd[988]: Server listening on :: port 22.
Jan 12 15:55:30 Sam-linux-server gdm-session-worker[1277]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Jan 12 15:55:30 Sam-linux-server gdm-session-worker[1277]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 12 15:55:34 Sam-linux-server seahorse-daemon[1387]: init gpgme version 1.1.8
Jan 12 15:57:22 Sam-linux-server sshd[997]: Server listening on 0.0.0.0 port 22.
Jan 12 15:57:22 Sam-linux-server sshd[997]: Server listening on :: port 22.
Jan 12 15:57:44 Sam-linux-server gdm-session-worker[1293]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Jan 12 15:57:44 Sam-linux-server gdm-session-worker[1293]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 12 15:57:47 Sam-linux-server seahorse-daemon[1405]: init gpgme version 1.1.8
Jan 12 16:00:26 Sam-linux-server sshd[997]: Server listening on 0.0.0.0 port 22.
Jan 12 16:00:26 Sam-linux-server sshd[997]: Server listening on :: port 22.
Jan 12 16:00:40 Sam-linux-server gdm-session-worker[1289]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Jan 12 16:00:40 Sam-linux-server gdm-session-worker[1289]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 12 16:00:44 Sam-linux-server seahorse-daemon[1401]: init gpgme version 1.1.8
Jan 12 16:10:54 Sam-linux-server su[1596]: Successful su for root by sam
Jan 12 16:10:54 Sam-linux-server su[1596]: + /dev/pts/0 sam:root
Jan 12 16:10:54 Sam-linux-server su[1596]: pam_unix(su:session): session opened for user root by sam(uid=1000)
Jan 12 16:11:47 Sam-linux-server su[1596]: pam_unix(su:session): session closed for user root
Jan 12 16:12:45 Sam-linux-server su[1624]: Successful su for root by sam
Jan 12 16:12:45 Sam-linux-server su[1624]: + /dev/pts/0 sam:root
Jan 12 16:12:45 Sam-linux-server su[1624]: pam_unix(su:session): session opened for user root by sam(uid=1000)
Jan 12 16:13:46 Sam-linux-server sudo:     root : TTY=pts/0 ; PWD=/ ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-server
Jan 12 16:14:42 Sam-linux-server su[1624]: pam_unix(su:session): session closed for user root
Jan 12 16:15:17 Sam-linux-server sudo:      sam : TTY=pts/0 ; PWD=/ ; USER=root ; COMMAND=/etc/init.d/ssh start
Jan 12 16:17:01 Sam-linux-server sudo:      sam : TTY=pts/0 ; PWD=/home/sam ; USER=root ; COMMAND=/etc/init.d/ssh start
Jan 12 16:17:01 Sam-linux-server CRON[1693]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 16:17:01 Sam-linux-server CRON[1693]: pam_unix(cron:session): session closed for user root
Jan 12 16:18:35 Sam-linux-server sshd[982]: Server listening on 0.0.0.0 port 22.
Jan 12 16:18:35 Sam-linux-server sshd[982]: Server listening on :: port 22.
Jan 12 16:18:50 Sam-linux-server gdm-session-worker[1279]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Jan 12 16:18:50 Sam-linux-server gdm-session-worker[1279]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 12 16:18:53 Sam-linux-server seahorse-daemon[1391]: init gpgme version 1.1.8
Jan 12 16:20:29 Sam-linux-server su[1542]: Successful su for root by sam
Jan 12 16:20:29 Sam-linux-server su[1542]: + /dev/pts/0 sam:root
Jan 12 16:20:29 Sam-linux-server su[1542]: pam_unix(su:session): session opened for user root by sam(uid=1000)
Jan 12 16:20:39 Sam-linux-server sudo:     root : TTY=pts/0 ; PWD=/home/sam ; USER=root ; COMMAND=/etc/init.d/ssh start
Jan 12 16:21:28 Sam-linux-server sudo:     root : TTY=pts/0 ; PWD=/home/sam ; USER=root ; COMMAND=/etc/init.d/ssh start
Jan 12 16:23:18 Sam-linux-server su[1542]: pam_unix(su:session): session closed for user root
Jan 12 16:23:24 Sam-linux-server gdm-session-worker[1279]: pam_unix(gdm:session): session closed for user sam
Jan 12 16:23:38 Sam-linux-server gdm-session-worker[1724]: pam_unix(gdm:session): session opened for user root by (uid=0)
Jan 12 16:23:38 Sam-linux-server gdm-session-worker[1724]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 12 16:23:42 Sam-linux-server seahorse-daemon[1839]: init gpgme version 1.1.8
Jan 12 16:22:21 Sam-linux-server sshd[2047]: Accepted password for root from 192.168.1.100 port 3475 ssh2
Jan 12 16:22:21 Sam-linux-server sshd[2047]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 16:22:28 Sam-linux-server sshd[2047]: pam_unix(sshd:session): session closed for user root
Jan 12 16:22:42 Sam-linux-server gdm-session-worker[1724]: pam_unix(gdm:session): session closed for user root
Jan 12 16:22:54 Sam-linux-server gdm-session-worker[2217]: pam_unix(gdm:session): session opened for user sam by (uid=0)
Jan 12 16:22:54 Sam-linux-server gdm-session-worker[2217]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Jan 12 16:22:57 Sam-linux-server seahorse-daemon[2329]: init gpgme version 1.1.8
Jan 12 17:01:27 Sam-linux-server sudo:      sam : TTY=pts/0 ; PWD=/home/sam ; USER=root ; COMMAND=/usr/bin/apt-get remove openssh-server
Jan 12 17:01:51 Sam-linux-server sshd[982]: Received signal 15; terminating.
Jan 12 17:02:17 Sam-linux-server sudo:      sam : TTY=pts/0 ; PWD=/home/sam ; USER=root ; COMMAND=/usr/bin/apt-get install openssh-server
Jan 12 17:02:28 Sam-linux-server sshd[2679]: Server listening on 0.0.0.0 port 22.
Jan 12 17:02:28 Sam-linux-server sshd[2679]: Server listening on :: port 22.
Jan 12 17:05:03 Sam-linux-server sshd[2706]: error writing /proc/self/oom_adj: Permission denied
Jan 12 17:05:03 Sam-linux-server sshd[2706]: error: Bind to port 22 on 0.0.0.0 failed: Permission denied.
Jan 12 17:05:03 Sam-linux-server sshd[2706]: error: Bind to port 22 on :: failed: Permission denied.
Jan 12 17:05:03 Sam-linux-server sshd[2706]: fatal: Cannot bind any address.
Jan 12 17:06:27 Sam-linux-server gdm-session-worker[2217]: pam_unix(gdm:session): session closed for user sam
Jan 12 17:06:40 Sam-linux-server gdm-session-worker[2791]: pam_unix(gdm:session): session opened for user root by (uid=0)
Jan 12 17:06:40 Sam-linux-server gdm-session-worker[2791]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Jan 12 17:06:43 Sam-linux-server seahorse-daemon[2906]: init gpgme version 1.1.8
Jan 12 17:07:12 Sam-linux-server sshd[3106]: Accepted password for sam from 192.168.1.100 port 3534 ssh2
Jan 12 17:07:12 Sam-linux-server sshd[3106]: pam_unix(sshd:session): session opened for user sam by (uid=0)
Jan 12 17:09:33 Sam-linux-server sshd[2679]: Received signal 15; terminating.
Jan 12 17:09:33 Sam-linux-server sshd[3262]: Server listening on 0.0.0.0 port 22.
Jan 12 17:09:33 Sam-linux-server sshd[3262]: Server listening on :: port 22.
Jan 12 17:09:43 Sam-linux-server gdm-session-worker[2791]: pam_unix(gdm:session): session closed for user root
Jan 12 17:17:01 Sam-linux-server CRON[3369]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 17:17:01 Sam-linux-server CRON[3369]: pam_unix(cron:session): session closed for user root
Jan 12 18:17:01 Sam-linux-server CRON[3374]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 18:17:01 Sam-linux-server CRON[3374]: pam_unix(cron:session): session closed for user root
Jan 12 19:17:01 Sam-linux-server CRON[3379]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 12 19:17:01 Sam-linux-server CRON[3379]: pam_unix(cron:session): session closed for user root
Jan 12 19:18:28 Sam-linux-server sshd[3106]: pam_unix(sshd:session): session closed for user sam
Jan 12 19:20:26 Sam-linux-server gdm-session-worker[3354]: pam_unix(gdm:auth): conversation failed
Jan 12 19:20:26 Sam-linux-server gdm-session-worker[3354]: pam_unix(gdm:auth): auth could not identify password for [sam]
Jan 12 19:20:33 Sam-linux-server gdm-session-worker[3393]: pam_unix(gdm:session): session opened for user root by (uid=0)
Jan 12 19:20:33 Sam-linux-server gdm-session-worker[3393]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Jan 12 19:20:36 Sam-linux-server seahorse-daemon[3495]: init gpgme version 1.1.8
Jan 12 20:02:20 Sam-linux-server sshd[3699]: Accepted password for root from 72.193.243.114 port 51989 ssh2
Jan 12 20:02:20 Sam-linux-server sshd[3699]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 20:03:26 Sam-linux-server sshd[3699]: pam_unix(sshd:session): session closed for user root
Jan 12 20:03:41 Sam-linux-server sshd[3777]: Accepted password for root from 72.193.243.114 port 52008 ssh2
Jan 12 20:03:41 Sam-linux-server sshd[3777]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 20:06:54 Sam-linux-server sshd[3869]: Accepted password for root from 72.193.243.114 port 52022 ssh2
Jan 12 20:06:54 Sam-linux-server sshd[3869]: pam_unix(sshd:session): session opened for user root by (uid=0)
Jan 12 20:06:55 Sam-linux-server sshd[3869]: subsystem request for sftp


```

---

### Post by endoglastic on 2010-01-12
Full Version here.
 ----------

---

### Post by YetAnother on 2010-01-13
There isn't anything in logs which shows login as sam fails when, you are logged in as sam. It shows a bunch of successful logins for user sam.

It is a bad idea to allow root ssh access. You might want to disable it. Also use something like fail2ban to thwart dictionary attacks. Also remove your logs from internet when you are done solving this problem(for security reasons)

---

### Post by endoglastic on 2010-01-13
Well, once i get it so when the computer is actually logged in as sam and not root, i can take root off the login. Becuase ssh only works when the actual computer is logged in as root. When its logged in as sam i cant connect to it. Thats what im trying to figure out.
 
> Also use something like fail2ban to thwart dictionary attacks.
 
I dont know what this means.

---

### Post by YetAnother on 2010-01-13
See [http://en.wikipedia.org/wiki/Fail2ban]("http://www.howtoforge.com/fail2ban_debian_etch")
For a howto
[http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

---

### Post by endoglastic on 2010-01-13
Ok that will be nice to have, but any idea on my other problem?

---

### Post by YetAnother on 2010-01-13
Your logs show you don't have a problem. Try this login as sam @ the machine. Try sshing as sam and if you fail, mail me the /var/log/auth.log 

You don't have to be logged in at the physical server either as root/sam for ssh to work. You just need to be a root/use sudo to start it. once started it runs in background and accepts ssh connections.

All your log shows is that your ssh failed to start when you were running as sam, soon after your reinstall. There probably wasn't any ssh running, so your logins were failing. 

[service ssh status] will tell you if your ssh is running or not.

---

### Post by endoglastic on 2010-01-13
> Try this login as sam @ the machine. Try sshing as sam and if you fail, mail me the /var/log/auth.log 
 
Thats what i originally posted it was doing. It would not ssh when i logged in as sam on the actual machine.
 
When i opened up putty, it wouldnt even give me "type a logon name and password", it would basically time out trying to connect to it and wouldnt even get to that part.
 
-------------------------------------------------

---

### Post by YetAnother on 2010-01-13
This step failed "sudo /etc/init.d/ssh start" so , there wasn't any ssh daemon running when you tried to login. 
Your logs show your set up is perfect and doesn't have any problems.

---

### Post by YetAnother on 2010-01-13
This step failed "sudo /etc/init.d/ssh start" so , there wasn't any ssh daemon running when you tried to login.

---

### Post by endoglastic on 2010-01-14
well i even type that in logged in to sam and went to terminal and did that as su, guess ill have to try it again.

---

