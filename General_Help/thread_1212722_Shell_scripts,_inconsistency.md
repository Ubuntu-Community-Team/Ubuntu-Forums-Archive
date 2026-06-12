---
title: "Shell scripts, inconsistency?"
date: 2009-07-14
forum: General Help
---

### Post by Jeinhor on 2009-07-14
Hi,

I created a script for checking my RAID array, (something) like this:

```
if [ `cat /proc/mdstat | grep -c [UU]` == 3 ]
then
     echo "OK"
else
     echo "FAIL"
fi
```

I then did 

```
chmod a+x raidcheck
```

I can now run that script by going either full path,

```
/home/myusername/raidcheck
```

or by dotslash:

```
./raidcheck
```

I scheduled my script with cron using 

```
crontab -e
```

but it always returned FAIL (which made me feel uneasy ;)). I couldn't understand why. But then I tried starting the script using sh instead, like this:

```
sh raidcheck
```

And that gave me some "syntax error" (or similar), and it also returned FAIL. So I changed the if-statement slightly, resulting in this:

```
if [ `cat /proc/mdstat | grep -c [UU]` -eq 3 ]
```

And NOW it worked using sh aswell. cron is probably using sh to launch the script, because now it's working.

Can anyone explain this to me?

Thanks in advance!

---

### Post by kpkeerthi on 2009-07-14
Add ```
#! /bin/bash
``` as the first line in your script and it would work consistently as it would, now, always be run by bash.

---

### Post by Jeinhor on 2009-07-14
Ok, thanks.

What was used instead of bash to run the script?

---

### Post by nikhilk on 2009-07-14
> **Jeinhor said:**
> What was used instead of bash to run the script?

sh stands for [Bourne]("http://en.wikipedia.org/wiki/Bourne_shell") shell while bash stands for the [Bourne-again]("http://en.wikipedia.org/wiki/Bash") shell.
You were running the script with the Bourne shell.

---

### Post by mcduck on 2009-07-14
> **nikhilk said:**
> sh stands for [Bourne]("http://en.wikipedia.org/wiki/Bourne_shell") shell while bash stands for the [Bourne-again]("http://en.wikipedia.org/wiki/Bash") shell.
You were running the script with the Bourne shell.

Actually the default shell (sh) in Ubuntu is [Dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). Bash is used as default interactive shell for users.

---

### Post by Jeinhor on 2009-07-14
> **nikhilk said:**
> sh stands for [Bourne]("http://en.wikipedia.org/wiki/Bourne_shell") shell while bash stands for the [Bourne-again]("http://en.wikipedia.org/wiki/Bash") shell.
You were running the script with the Bourne shell.

Thanks for sorting that out.

> **mcduck said:**
> Actually the default shell (sh) in Ubuntu is [Dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). Bash is used as default interactive shell for users.

So bash for interactive users, dash otherwise. cron is using dash and not sh then (if I do not specify it)?

---

### Post by nikhilk on 2009-07-14
> **Jeinhor said:**
> Thanks for sorting that out.


You are welcome!

> **Jeinhor said:**
> cron is using dash and not sh then (if I do not specify it)?

IIRC, bash uses the shell specified in /etc/passwd as the default shell (I am not sure what that is by default).

You can use the SHELL environment variable in your crontab file to explicitly specify a shell. Or you can explicitly specify the shell to be used to execute a script in the cron job.
My advise is be explicit by using one of the above two methods and avoid any confusion.

---

### Post by Jeinhor on 2009-07-14
Ok, got it! Thread solved =) Thanks!

---

### Post by mcduck on 2009-07-14
> **Jeinhor said:**
> Thanks for sorting that out.



So bash for interactive users, dash otherwise. cron is using dash and not sh then (if I do not specify it)?

Even specifying it wouldn't make difference. /bin/sh is just a symbolic link pointing to /bin/dash. In other words, Dash has replaced the Bourne Shell in Ubuntu.

---

