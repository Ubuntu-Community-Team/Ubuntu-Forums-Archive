---
title: "running script on wake/thaw never happens! help!"
date: 2011-08-11
forum: General Help
---

### Post by azredwing on 2011-08-11
Hi all,

I'm running a Thinkpad W510 with Ubuntu 11.04 x64. Since I'm using the nvidia driver, my computer won't automagically switch display types when I'm docked/undocked/using an external screen. 

I've used disper and auto-disper to get around that. One annoyance I've had is that if I were to suspend my computer while it's docked (when docked, the laptop monitor blanks out and my two external monitors are up), undock it, then unsuspend it, the previous display configuration is kept (i.e., my laptop monitor is still blanked out and the computer is attempting to send signal to the two external monitors - can confirm by redocking after wakeup.)

So I wrote this script and stuck it in /etc/pm/sleep.d:
```

#!/usr/bin/sh

case "$1" in
    thaw | resume )
        auto-disper --change
        ;;
esac

```

The --change parameter forces disper to update the display configuration based on the hardware connected to it.

This script doesn't do anything on wake - when I dock my laptop, suspend, undock, wake up, the laptop screen is black. Putting the laptop back in the dock sends signal to my external monitors. (Before anyone asks, I made a symlink to auto-disper, and set it to look for profiles in my specific home directory - I can run as root and execute the auto-disper script properly.)

It turns out this script is not even executing:

```

#!/usr/bin/sh

case "$1" in
    thaw | resume )
        echo "AM I ALIVE?" > /home/azredwing/autodisper_on_wake.txt
        auto-disper --change
        ;;
esac

```

The file autodisper_on_wake.txt is never made.

Any ideas what's going on? (Yes, a+x permissions are enabled on the wake script.) Thanks for the help!

---

### Post by Toz on 2011-08-11
> #!/usr/bin/sh
Doesn't exist on my box. Does it exist on yours? You could always try:
> #!/bin/bash

---

### Post by azredwing on 2011-08-15
> **Toz said:**
> Doesn't exist on my box. Does it exist on yours? You could always try:

Oops ^______^ I've been working on scripting for Android way too much, and in there it's #!/system/bin/sh. Getting myself confused.

Anyhow, it now creates autodisper_on_wake.txt, but still doesn't change my screen immediately. That's probably more of a disper problem.. 

thanks for the help!

---

### Post by Toz on 2011-08-15
Maybe it doesn't know about the display. Try:
```
DISPLAY=:0.0 auto-disper --change
```

---

### Post by azredwing on 2011-08-15
> **Toz said:**
> Maybe it doesn't know about the display. Try:
```
DISPLAY=:0.0 auto-disper --change
```

no dice :( thanks for the help, though.

---

### Post by Toz on 2011-08-15
Have a look at this: [http://askubuntu.com/questions/42741/how-to-automatically-switch-monitors-with-my-laptop-dock]("http://askubuntu.com/questions/42741/how-to-automatically-switch-monitors-with-my-laptop-dock"). Its similar and the code shows how to export the X session so that disper has access to it.

---

### Post by sbraz on 2011-08-15
> **azredwing said:**
> So I wrote this script and stuck it in /etc/pm/sleep.d:
```

#!/usr/bin/sh

case "$1" in
    thaw | resume )
        auto-disper --change
        ;;
esac

```

mine runs but looks different:
```
#!/bin/bash
case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)
#
#
####add commands here
#
#
        ;;
    *)
        ;;
esac
exit $?
```
i don't know why it's written like this, i just copied it from somewhere.

---

### Post by azredwing on 2011-08-16
> **Toz said:**
> Have a look at this: [http://askubuntu.com/questions/42741/how-to-automatically-switch-monitors-with-my-laptop-dock]("http://askubuntu.com/questions/42741/how-to-automatically-switch-monitors-with-my-laptop-dock"). Its similar and the code shows how to export the X session so that disper has access to it.

Ooh, this could be good! Will read and get back to you.

---

