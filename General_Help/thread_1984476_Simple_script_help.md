---
title: "Simple script help"
date: 2012-05-21
forum: General Help
---

### Post by lisanels47 on 2012-05-21
I'm writing a script to determine if my laptop is at home, or one of my customer sites.  

In the below code, I want to check the broadcast address to determine if the computer is on one of my 192.168.5.0 addresses.  But this code doesn't work.  No matter what I change the Bcast address to, it comes out the same.  What am I doing wrong?


#!/bin/bash
PATH=/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/home/lisa/bin
#Update the host file if not already done.
ifconfig | grep Bcast:192.168.5.255 &> /dev/null
if [ $? = "0" ]; then
	echo "Computer is at home."
		else
	echo "Computer is not at home."
                fi

---

### Post by diesch on 2012-05-21
You set $PATH so it doesn't contain */sbin* hence the shell doesn't find */sbin/ifconfig *when searching for *ifconfig*

Either include */sbin* in $PATH or use* /sbin/ifconfig* instead of just *ifconfig*

---

