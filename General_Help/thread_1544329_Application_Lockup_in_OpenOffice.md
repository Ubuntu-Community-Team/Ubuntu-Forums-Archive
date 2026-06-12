---
title: "Application Lockup in OpenOffice"
date: 2010-08-02
forum: General Help
---

### Post by irv on 2010-08-02
There is a bad bug in OpenOffice that keeps giving me a hard lock. I can not even shut down the program, I need to force a reboot. I can make it happen repetitively. Anytime I am working on a presentation in OpenOffice Impress an am working with sound files this happens. If I am moving the sound file icon around on the slide it randomly locks up the file I have open. Another way is resizing the icon and it will also lock it up.
Has anyone else having this problem?

---

### Post by Smart Viking on 2010-08-02
can you not even kill it in tty with

```
kill -9 PID
```
? :)

---

### Post by irv on 2010-08-02
> **Smart Viking said:**
> can you not even kill it in tty with

```
kill -9 PID
```
? :)
How do I find the job ID?
```
irv@irv-laptop:~$ kill -9 PID
bash: kill: PID: arguments must be process or job IDs

```

---

### Post by Smart Viking on 2010-08-02
> **irv said:**
> How do I find the job ID?
```
irv@irv-laptop:~$ kill -9 PID
bash: kill: PID: arguments must be process or job IDs

```

hi sorry for answering late, you can find job PIDs with this command:

```
ps ax
```
the PID is the first line of numbers

and to make it easier you could do this:

```
ps ax | grep -i open
```

which will show the processes with "open" in it, and the first number of numbers are "PID", so if the PID was to be lets say "20161", then you would do this to kill it(the "-9" means that it will kill it with maximum force.)

```
kill -9 20161
```

and thats it, if you didn't understand or something went wrong, you could enter the following command and see if that works:

```
pkill -9 offi
```
(should do that same thing) :)

---

### Post by irv on 2010-08-04
Thanks for the help, I will try this next time it locks up.

---

### Post by Hagar Delest on 2010-08-05
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

