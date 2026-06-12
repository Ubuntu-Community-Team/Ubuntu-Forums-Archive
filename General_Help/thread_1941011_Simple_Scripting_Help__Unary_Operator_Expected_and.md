---
title: "Simple Scripting Help :: Unary Operator Expected and Too Many Arguments"
date: 2012-03-14
forum: General Help
---

### Post by own3mall on 2012-03-14
What's wrong with my if statement?  It states that it expects a unary argument and that there are too many parameters.  Why?

```

COUNT=gksudo find /var/log/syslog -exec grep -c -i "DY-001" {} \;
echo $COUNT

COUNTC=gksudo find /var/log/syslog -exec grep -c -i "ES000001" {} \;
echo $COUNTC

if [ $COUNT -gt 0 -o $COUNTC -gt 0 ];
then

```

I've tried everything... I'm so confused.  Seems as if my variables are not ints.

---

### Post by matt_symes on 2012-03-14
Hi

First things first.

Why the find command and gksudo (do you not have admin access) ?

```
grep -c -i "ES000001" /var/log/syslog
```

Second you need the output of the grep command and not the command itself.

Try this

```

!#/bin/sh

COUNT=$(grep -c -i "DY-001" /var/log/syslog);
echo $COUNT

COUNTC=$(grep -c -i "ES000001" /var/log/syslog);
echo $COUNTC

if [ $COUNT -gt 0 -o $COUNTC -gt 0 ];
then
    echo "1";
fi

```

Kind regards

---

### Post by own3mall on 2012-03-15
__Thanks Matt!  Works perfectly.  I was running my original script as root (sudo -i from my normal account) and it was still telling me I didn't have permissions to access /var/log/syslog

Thus, I added the gksudo, but my new script thanks to you doesn't require that.

Also, do you know how I can find out the precise time when the /var/log/syslog gets rotated daily?

---

### Post by matt_symes on 2012-03-15
Hi

> **own3mall said:**
> __Thanks Matt!  Works perfectly.  I was running my original script as root (sudo -i from my normal account) and it was still telling me I didn't have permissions to access /var/log/syslog

Thus, I added the gksudo, but my new script thanks to you doesn't require that.

That make sense. If your a member of the adm group you should not need to run sudo to view the logs.

```
matthew@matthew-Aspire-7540:~$ ls -l /var/log/syslog
-rw-r----- 1 syslog **adm** 2712 Mar 15 09:45 /var/log/syslog
matthew@matthew-Aspire-7540:~$
```

> Also, do you know how I can find out the precise time when the /var/log/syslog gets rotated daily?

I'm not 100% sure. It will be cron of course so check that out. Maybe it's anacron after a reboot.

Kind regards

---

