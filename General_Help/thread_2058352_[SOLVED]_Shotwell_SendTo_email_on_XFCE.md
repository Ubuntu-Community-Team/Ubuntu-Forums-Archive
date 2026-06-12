---
title: "[SOLVED] Shotwell SendTo email on XFCE"
date: 2012-09-15
forum: General Help
---

### Post by celem on 2012-09-15
I have a pure Xfce system and installed the shotwell photo manager. I discovered that shotwell is hard coded to send photos via the Gnome nautilus-sendto feature, which is absent in Xfce.

I solved the problem by creating a small bash script that passes the correct arguments to and executes Xfce's Thunar/sendto feature. Works like a champ!

```

#!/bin/bash
# Edward Comer
# Enables Shotwell to SendToEmail in XFCE system. Shotwell depends on
# nautilus-sendto (in an executable path) to function, which is missing
# in a pure XFCE installation. This script is named nautilus-sendto
# and placed in /usr/local/bin and marked executable

LOGFILE=/tmp/nautilus-sendtolog.txt

echo Inside nautilus-sendto >$LOGFILE
echo Number of arguments passed: $# >>$LOGFILE
echo Passed arguments are: >>$LOGFILE
echo $@ >>$LOGFILE
SENDTOCMD=`grep Exec /usr/share/Thunar/sendto/thunar-sendto-email.desktop`
echo "SENDTOCMD="$SENDTOCMD >>$LOGFILE
SENDTOEXEC=`echo ${SENDTOCMD:5}`
SENDTOEXEC=`echo ${SENDTOEXEC// %F/}`
if [ -z "$SENDTOEXEC" ]
then
  echo "\$SENDTOEXEC is null." >>$LOGFILE
else
	echo "SENDTOEXEC="$SENDTOEXEC >>$LOGFILE
	echo Executing $SENDTOEXEC $@ >>$LOGFILE
	$SENDTOEXEC $@
fi
echo Exiting nautilus-sendto >>$LOGFILE
exit


```

P.S.: Shotwell has a [bug"]bug]("https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1002537?comments=all) where it doesn't always email multiple selected photos. This is a shotwell bug that I have verified with test scripts. Simply selecting multiple photos will only result in one photo being mailed. To get around the bug, the only known workaround is to transform them at the SendTo dialog by scaling them. If they are already too small to scale, the bug will remain, thus scaling will have to occur to workarounf the bug. See Bug#1002537

---

### Post by dc46and2 on 2013-01-09
Thanks for sharing!  The script works great, but sadly the gmail client (which I use exclusively) doesn't support attachments.  Doh!

---

### Post by celem on 2013-01-09
I also use gmail, although not exclusively, and I send attachments using this method. Although I use the web interface for my normal mail interaction, for this script I use thunderbird and the attachments go out just fine.


> **dc46and2 said:**
> Thanks for sharing!  The script works great, but sadly the gmail client (which I use exclusively) doesn't support attachments.  Doh!

---

### Post by celem on 2013-01-09
FYI - the shotwell bug mentioned in my post is fixed in their current unstable version. See:
[http://redmine.yorba.org/issues/5827]("http://redmine.yorba.org/issues/5827")

---

