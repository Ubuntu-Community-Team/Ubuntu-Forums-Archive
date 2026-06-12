---
title: "Manual method to trigger command-not-found search"
date: 2010-01-15
forum: General Help
---

### Post by bostonvaulter on 2010-01-15
I really like that in Ubuntu when you type in a command that's not on the system you get a message saying the package that provides that command. Unfortunately it also slows down my system, so I would like a way to trigger this manually. Something like search-command command-I-dont-have

Is there any way to do this?

I'm using Ubuntu 9.04 under andLinux but would also like to use this on a regular Ubuntu 9.04 install.

---

### Post by sisco311 on 2010-01-19
Edit the /etc/bash.bashrc and comment out the command-not-found entry:
```
# if the command-not-found package is installed, use it
**#**if [ -x /usr/lib/command-not-found ]; then
**#**        function command_not_found_handle {
                # check because c-n-f could've been removed in the meantime
**#**                if [ -x /usr/lib/command-not-found ]; then
**#**                   /usr/bin/python /usr/lib/command-not-found -- $1
**#**                   return $?
**#**                else
**#**                   return 127
**#**                fi
**#**        }
**#**fi
```

Log out from the terminal and log back in.

Edit your ~/.bashrc file and append it with:
```


if [ -x /usr/lib/command-not-found ]; then
        function **cnf** {
                # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
                   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
                else
                   return 127
                fi
        }
fi

```

source the file:
```
. ~/.bashrc
```

usage:
```
**cnf** command-name
```

---

### Post by bostonvaulter on 2010-01-19
Thanks! This works perfectly. Hopefully it will be useful to others as well.

---

### Post by sisco311 on 2010-01-19
> **bostonvaulter said:**
> Thanks! This works perfectly. Hopefully it will be useful to others as well.

You are welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

