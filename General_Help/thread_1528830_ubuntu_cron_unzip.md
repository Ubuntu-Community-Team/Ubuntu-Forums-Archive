---
title: "ubuntu cron unzip"
date: 2010-07-11
forum: General Help
---

### Post by andre.ukit on 2010-07-11
Hello.
Problem is what unzip command, finish before all unzip is done.
```

#!/bin/dash
cd /home/ftpuser/www_base/
if [ -f www_base.zip ]
then
/bin/rm  -rf /home/ftpuser/www_base/www_base/
/usr/bin/unzip www_base.zip 
/bin/rm  www_base.zip
fi
```

in archive www_base.zip is around 10k files.
but unzip command, extract just about 100.
And when I run this script manual, it work perfectly, but if it's run from cron, unzip not all files.
What can be a problem?

---

### Post by new_tolinux on 2010-07-11
I don't have any idea about your script, but the first thing that I see is:
```

#!/bin/dash
```As far as I know, that should be:
```
#!/bin/bash
```

Although I'm absolutely not sure that's the reason unzip fails when using cron.

---

### Post by DaithiF on 2010-07-11
Hi,
cron doesn't like jobs that generate a lot of stdout output, beyond a certain number of bytes and the process terminates.  unzip will echo the name of every file it is unzipping to stdout, you can suppress this either by using the -q flag, or else by redirecting the output (to /dev/null for example).

---

### Post by andre.ukit on 2010-07-11
Thanks.
-q flag solve my problem.

---

