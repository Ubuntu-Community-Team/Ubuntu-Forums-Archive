---
title: "how to clear the screen in a non-gui login"
date: 2006-05-24
forum: General Help
---

### Post by jeisma on 2006-05-24
hello!

doing this (thanks bluenova for the link)

[http://ubuntuforums.org/showthread.php?t=175885&highlight=init+runlevel](http://ubuntuforums.org/showthread.php?t=175885&highlight=init+runlevel)

i now have a no-gui login. but i want to clear the screen right before presenting the login prompt (dont want to have the "starting" this.. "starting" that.. showing before the login).  and perhaps have my own custom messages right above the login prompt.

help pls?


thanks!

joey

---

### Post by cskeide on 2006-05-24
Haven't tried this myself, but you should be able to use /etc/rc.local to clear the screen.

Edit /etc/rc.local and add clear > /dev/tty1. Mine would look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
clear > /dev/tty1

exit 0

```

If you want custom text above the login prompt you can edit /etc/issue

---

