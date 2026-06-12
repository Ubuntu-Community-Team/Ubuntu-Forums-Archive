---
title: "keep processes running"
date: 2010-08-20
forum: General Help
---

### Post by goltoof on 2010-08-20
How do I make sure a process stays open?

ie, if the process isn't running the script should re-open it. But if it's already open the script does nothing.  The script should check to make sure the process is running every hour.

Sometimes I'll close an app, pidgin for example, by accident and need the system to make sure it stays open.

Cron will do this easy, but how to do this without opening duplicate processes?

---

### Post by goltoof on 2010-08-23
does this question make sense?

---

### Post by spibou on 2010-08-23
Yes , the question makes perfect sense. Here is a simple way which doesn't use cron at all:```

#!/bin/sh

# NOT TESTED

if [ -e "$HOME"/really-stop-application ] ; then
    /bin/rm "$HOME"/really-stop-application
fi

while : ; do
    # start your application here
    if [ -e "$HOME"/really-stop-application ] ; then
        exit 0
    fi
done
```
The above is a template script , you will need to modify the line **# start your application here** with the command which actually starts the application. **Don't put the application in the background** because if you do the script will keep starting new copies. What the script does is create an infinite loop so if your application gets terminated it will be restarted immediately. If you want your application to finish and not get restarted then you do first```
touch "$HOME"/really-stop-application
```and then you stop it.

---

### Post by goltoof on 2010-08-27
Thanks a bunch.

---

### Post by WorMzy on 2010-08-27
```
#!/bin/bash
while true; do
pidgin
done
```

This simple script launches pidgin, then waits until it's closed, then repeats itself. It'll keep launching pidgin until the script is killed.

---

