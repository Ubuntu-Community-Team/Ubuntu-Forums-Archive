---
title: "Running a command on wake-up from suspend"
date: 2009-11-22
forum: General Help
---

### Post by allanlewis on 2009-11-22
I am running MythTV and have found that mythtv-backend prevents the computer from suspending. So, I wrote a simple script:
```
#!/bin/sh
gksudo stop mythtv-backend
gksudo pm-suspend
```
This works perfectly and the computer resumes correctly (most of the time). However, I now need to restart the MythTV backend, which I currently do manually, via a desktop launcher that runs:
```
gksudo restart mythtv-backend
```
I would like to be able to have this command (and maybe others) run when the machine resumes from suspend. I have read elsewhere about /etc/pm/sleep.d but I'm not sure how to put a "root" command in there, such as restarting a service...

---

### Post by Zorael on 2009-12-04
Well, scripts in **/etc/pm/*.d/** should be run with root privileges, so just omit the gksudos.
```
#!/bin/sh

# Arguments can be:
#    "suspend suspend"
#    "resume suspend"
#    "thaw hibernate"

case "$1" in
        "suspend"
                stop mythtv-backend
                ;;
        "resume"
                start mythtv-backend
esac
```
And save it as **/etc/pm/sleep.d/90_mythtv-backend-fix** or something.

---

### Post by allanlewis on 2009-12-04
> **Zorael said:**
> Well, scripts in **/etc/pm/*.d/** should be run with root privileges, so just omit the gksudos.
Thanks!

---

### Post by nourathar on 2011-03-22
Thanks, I wanted to do something else on resume and wondered where the script should go..

---

### Post by theWrkncacnter on 2012-01-31
Hey, I don't really understand this stuff, but I'd like to run a command every time the computer wakes from sleep or hibernate. Should I modify #2 in this thread and save it as "/etc/pm/sleep.d/90_psmouse" ?

It would be great if I understood what was happening here too.
Thanks for any answers to this question.

```
#!/bin/sh

# Arguments can be:
#    "suspend suspend"
#    "resume suspend"
#    "thaw hibernate"

case "$1" in
        "suspend"
                sudo modprobe -r psmouse; sleep 2; sudo modprobe psmouse

                ;;
        "resume"
                sudo modprobe -r psmouse; sleep 2; sudo modprobe psmouse

esac
```

---

