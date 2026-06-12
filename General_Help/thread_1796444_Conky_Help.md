---
title: "Conky Help"
date: 2011-07-03
forum: General Help
---

### Post by kainalu on 2011-07-03
Hey All,

I have a conky setup that includes an FTP monitor. I'm kind of new at conky. I would like the FTP monitor to show FTP ACTIVE in red and STANDBY in orange. How can this be accomplished?
EDIT : Everything currently works except for the colors.

 I have this script here : 
```

#!/bin/sh
# Run ssh and ftp connections check
#

while true; do

if netstat -a |grep ESTABLISHED|egrep 'ssh|ftp'
then
	    echo FTP ACTIVE > /tmp/connects.out

else
           echo "STANDBY" > /tmp/connects.out

fi

sleep 3m
done

```

and this line : 

```

FTP : ${alignr}${execi 30 cat /tmp/connects.out}

```

Thanks for looking!

---

### Post by Habitual on 2011-07-03
tcp_portmon port_begin port_end item (index) 

from [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Here's a port monitor script I wrote for conky, you can use that as a starting point. :)

conky -c x.txt to run it.

---

### Post by kainalu on 2011-07-04
Habitual, That script is really cool, but just a little overkill for what I need. I really just want an icon that changes color. I found the above script, and it works great, but I don't know how to get conky to change the color based on the status. 


I just want it to say :

"FTP : In Use" in red when people are connected -or-
FTP : Standby" in orange or green when it is idle.

I use the FTP server as a media server. Only used for movies and such.

---

### Post by kainalu on 2011-07-04
This works great :

(DELETED, SEE BELOW)

---

### Post by Habitual on 2011-07-04
kainalu:

Glad you found a solution for this.
As for overkill, that's me, sorry about that. My sole motive was to provide you with motivation to "fix it yourself".

+1 

Have a Great Day.

---

### Post by kainalu on 2011-07-04
No need to apologize Habitual. Thanks for all the help!

My final helper script : 

```

#!/bin/bash
# Run ssh and ftp connections check

while true; do

if ps aux | grep proftpd | egrep "RETR"
then
		rm -f /tmp/ftp.down
		rm -f /tmp/ftp.off
		echo "ACTIVE" > /tmp/ftp.on
		

else
		rm -f /tmp/ftp.down
		rm -f /tmp/ftp.on
		echo "Standby" > /tmp/ftp.off

fi

if /etc/init.d/proftpd status | grep "currently running"

then
	echo
else
	rm -f /tmp/ftp.off
	rm -f /tmp/ftp.on
	echo "ERROR" > /tmp/ftp.down

fi

if netstat -na |grep ESTABLISHED|egrep '11:22'
then
		rm -f /tmp/ssh.down
		rm -f /tmp/ssh.off
		echo "ACTIVE" > /tmp/ssh.on
		

else
		rm -f /tmp/ssh.down
		rm -f /tmp/ssh.on
		echo "Standby" > /tmp/ssh.off

fi

if /etc/init.d/ssh status | grep "sshd is running"

then
	echo
else
	rm -f /tmp/ssh.off
	rm -f /tmp/ssh.on
	echo "ERROR" > /tmp/ssh.down

fi

sleep 1m

done

```

and in conkyrc :
```

FTP : ${color red}${execi 30 cat /tmp/ftp.down}${color}${color green}${alignc}${execi 30 cat /tmp/ftp.off }${color}${color orange}${alignr}${execi 30 cat /tmp/ftp.on}${color}
SSH : ${color red}${execi 30 cat /tmp/ssh.down}${color}${color green}${alignc}${execi 30 cat /tmp/ssh.off }${color}${color orange}${alignr}${execi 30 cat /tmp/ssh.on}${color}

```

---

