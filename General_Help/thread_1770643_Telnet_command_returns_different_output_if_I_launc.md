---
title: "Telnet command returns different output if I launch it from cron"
date: 2011-05-29
forum: General Help
---

### Post by Cheesehead on 2011-05-29
Learning about sockets...

I have a test socket on a server. If I connect to it using telnet, I get exactly the response I expect. So I know the socket works, and the script on the server works:
```
my-desktop:~$ telnet 192.168.1.1 3333
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
RAM:    90 % Free ( 2793 M free, 3082 M total)
Connection closed by foreign host.

```

And if I script it, I get almost the same response from Telnet, but still a valid response from the socket. So I know that my script works:
```

#!/bin/bash
telnet 192.168.1.1 3333

```

```
my-desktop:~$ sh socket-test.sh
Connection closed by foreign host.
Server RAM:    90 % Free ( 2797 M free, 3082 M total)

```

But if I launch the script from an /etc/cron.d/ crontab job, the output is different. I get the telnet output, but nothing from the socket. Clearly the cron job is running, so it's not a cron issue:
```
me:~$ cat /etc/cron.d/socket-test-crontab
# Cron job to test the server socket

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

* * * * * me /home/me/socket-test.sh > /tmp/socket-test-output 2>&1

```
Here's the cronjob output:
```
me:~$less /tmp/socket-test-output
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
Connection closed by foreign host.

```

Question: How can I get the socket output if I launch the script from the cron job?

---

### Post by sanderj on 2011-05-29
Possible causes:
telnet and thus script is closed before the output is received
or
no explicit close (so maybe waiting for timeout), so the next telnet is overwriting the previous telnet output?

Anyway: ways to solve this, I would write:
- a python script using telnetlib (see [http://docs.python.org/release/2.5.2/lib/telnet-example.html](http://docs.python.org/release/2.5.2/lib/telnet-example.html)), or
- an expect script generated using autoexpect
Both will be a few lines (without error checking)


HTH

---

### Post by Cheesehead on 2011-05-29
Aha! It's not my scripting, it's not cron. It's a known issue with Telnet.
Telnet doesn't write it's activity beyond open/close to stdout without jumping through hoops.

Happily, more searching did find some good solutions, like using netcat instead.

But I'm going with a real fun hack:
```

#!/bin/bash
exec 3<>/dev/tcp/192.168.1.1/11105
cat <&3 > /tmp/socket-test-output

```
And my favorite output is back, even when trigerred by cron.

---

