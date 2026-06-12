---
title: "put off lcd-screen of laptop"
date: 2012-03-04
forum: General Help
---

### Post by 001neeraj on 2012-03-04
Hi, in my HP laptop, there is no hot key to put off lcd screen. But i found a shell script "screenblank.sh" in the directory /etc/acpi. I just copied it to my home folder and executed from a terminal. It is working-lcd screen went off. Then i bound this script to a key combination as:```
sh ~/screenblank.sh
```The problem is: This script is working only when there is a terminal is open. I am not running script from the terminal. Yet in the background, there need a terminal. My script is given below:
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
    . /usr/share/acpi-support/screenblank
    fi
done
```Try to help me....

---

