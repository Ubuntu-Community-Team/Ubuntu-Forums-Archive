---
title: "Cron not working in Hardy (and no error message)"
date: 2009-09-21
forum: General Help
---

### Post by Schuenemann on 2009-09-21
Hey,

I can't get cron to work in Ubuntu Hardy.

My tasks:
```
$ crontab -l
# m h  dom mon dow   command
* * * * * mkdir ~/`date +%H:%M`
```

```
$ ps aux | grep cron
root      6990  0.0  0.0   1924   680 ?        Ss   08:37   0:00 /usr/sbin/anacron -s
root      7018  0.0  0.0   2100   716 ?        Ss   08:37   0:00 /usr/sbin/cron
root      8845  0.0  0.0   1772   488 ?        S    08:42   0:00 /bin/sh -c nice run-parts --report /etc/cron.daily
root      8846  0.0  0.0   1700   572 ?        SN   08:42   0:00 run-parts --report /etc/cron.daily
root      8857  0.0  0.0   1772   520 ?        SN   08:42   0:00 /bin/sh /etc/cron.daily/apt
```

The task does not run and there is nothing in my mail.


In my home computer it ran just fine, but in this one it doesn't.

Thanks.

---

### Post by DaithiF on 2009-09-21
Hi, try escaping the '%' characters in the date command with a '\' character.

```
* * * * * mkdir ~/`date +\%H:\%M`
```

from crontab manpage:
> The  entire  command  portion  of the line, up to a newline or %
       character, will be executed by /bin/sh or by the shell specified in the
       SHELL  variable of the crontab file.  Percent-signs (%) in the command,
       unless escaped with backslash (\), will be changed into newline charac&#8208;
       ters,  and  all  data  after the first % will be sent to the command as
       standard input.

---

### Post by Schuenemann on 2009-09-21
Thanks, but that didn't do it.
Actually I've put that task just for testing. The real task is a shell script execution.

I changed to mkdir ~/aaa and it was not created either.


Still not solved.

---

### Post by Schuenemann on 2009-09-25
I found this in /var/log/messages:
> Sep 25 11:23:01 work kernel: [10078.613931] cron[11530]: segfault at 00000000 eip 00000000 esp bfa370ac error 4
Sep 25 11:24:01 work kernel: [10138.570875] cron[11546]: segfault at 00000000 eip 00000000 esp bfa370ac error 4
Sep 25 11:25:01 work kernel: [10198.537402] cron[11567]: segfault at 00000000 eip 00000000 esp bfa370ac error 4
Sep 25 11:26:01 work kernel: [10258.496643] cron[11581]: segfault at 00000000 eip 00000000 esp bfa370ac error 4
Sep 25 11:27:01 work kernel: [10318.459756] cron[11613]: segfault at 00000000 eip 00000000 esp bfa370ac error 4
Sep 25 11:28:01 work kernel: [10378.423390] cron[11638]: segfault at 00000000 eip 00000000 esp bfa370ac error 4


Edit: same in syslog.


Thanks

---

### Post by DaithiF on 2009-09-25
a shot in the dark, but could be:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=484122](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=484122)

possible solution from that thread, add the line:
```
@include common-pammount
```
to /etc/pam.d/cron

---

### Post by Schuenemann on 2009-09-25
I tried and it didn't help. The problem in that thread seems to be related to mount of encrypted partitions.

---

