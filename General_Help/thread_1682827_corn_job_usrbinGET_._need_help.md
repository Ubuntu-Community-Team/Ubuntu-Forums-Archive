---
title: "corn job /usr/bin/GET . need help"
date: 2011-02-06
forum: General Help
---

### Post by alan889999 on 2011-02-06
I bought a program which request me to run a corn job

and the command is like

0 * * * * /usr/bin/GET [http://www.domain.com/cron.php](http://www.domain.com/cron.php)

But when i 
/usr/bin/GET [http://www.domain.com/cron.php](http://www.domain.com/cron.php)
 to test

i got 
-bash: /usr/bin/GET: No such file or directory

please help me to solve this problem

thx

---

### Post by baqar on 2011-02-06
Which program :confused:

---

### Post by alan889999 on 2011-02-06
it is a wordpress plguin backlink energizer. and required me to do a corn job

But i found that ubuntu don't have a GET command

---

### Post by CharlesA on 2011-02-06
See here:
[http://manpages.ubuntu.com/manpages/gutsy/man1/lwp-request.1p.html](http://manpages.ubuntu.com/manpages/gutsy/man1/lwp-request.1p.html)

---

### Post by alan889999 on 2011-02-06
This looking like very difficult to make it work

so after install i should

type"
lwp-request -m <method> [http://www.domain.com/cron.php](http://www.domain.com/cron.php)

"

is this correct?

what is the method . i don't get it ??

---

### Post by firebird_1979 on 2011-02-06
You might mean the program "wget", which is a commandline download manager. It can download files off the Internet etc.

GET is not a program (as far as I know).

---

### Post by alan889999 on 2011-02-06
this plugin ask me to set a corn job
0 * * * * /usr/bin/GET [http://www.domain.com/wp-content/plugins/energizer/cron.php](http://www.domain.com/wp-content/plugins/energizer/cron.php)

this is the tutor. but i don't have cpanel in my vps server.
[http://www.screencast.com/users/AndyFletcher/folders/Jing/media/2708aa02-96d7-46b3-be3a-ab1846dd19c2](http://www.screencast.com/users/AndyFletcher/folders/Jing/media/2708aa02-96d7-46b3-be3a-ab1846dd19c2)


here
[http://support.hostgator.com/articles/cpanel/what-do-i-put-for-the-cron-job-command](http://support.hostgator.com/articles/cpanel/what-do-i-put-for-the-cron-job-command)

Command to GET a remote file:

---

### Post by CashCostello on 2011-12-10
GET is a part of the libwww-perl package.

---

