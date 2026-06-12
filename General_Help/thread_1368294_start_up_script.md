---
title: "start up script"
date: 2009-12-30
forum: General Help
---

### Post by izghitu on 2009-12-30
Hi,

I have Ubuntu 9.10

I want to set up a start up script that is executed last when the server boots and asks for user input/performs some tasks.

I've added the script to /etc/init.d/local and made it executable using:
update-rc.d local defaults 80

When the server boots, I do not see anything on the screen and no user input is requested although the script is executed.

If I add a reboot to the script to the end of the file after user input requests, the server is rebooted regardless of the "read" commands.

Am I doing something wrong?

Please help

Thanks

---

### Post by QLee on 2009-12-30
> **izghitu said:**
> Hi,

I have Ubuntu 9.10

I want to set up a start up script that is executed last when the server boots and asks for user input/performs some tasks.

I've added the script to /etc/init.d/local and made it executable using:
update-rc.d local defaults 80

When the server boots, I do not see anything on the screen and no user input is requested although the script is executed.

If I add a reboot to the script to the end of the file after user input requests, the server is rebooted regardless of the "read" commands.

Am I doing something wrong?

Please help

Thanks

It seems to me that when people ask for help on why a script isn't working, the people who post the script get lots better advice on why it isn't working.

---

### Post by izghitu on 2009-12-30
> **QLee said:**
> It seems to me that when people ask for help on why a script isn't working, the people who post the script get lots better advice on why it isn't working.

```
#!/bin/bash

clear # the screen is not cleared

echo qwerty # this is not printed on the screen
read n # no user input appeares

reboot # the server is rebooted
```

---

### Post by izghitu on 2010-01-01
Ok, I solved this by adding this to the beginning of the script:
```
exec > /dev/tty1 2>&1 < /dev/tty1
```

---

