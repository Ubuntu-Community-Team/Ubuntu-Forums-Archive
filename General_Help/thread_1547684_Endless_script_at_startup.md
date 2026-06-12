---
title: "Endless script at startup"
date: 2010-08-07
forum: General Help
---

### Post by dsamvelyan on 2010-08-07
Hi everyone

Sometimes I need remotely connect to my computer, but my router gains IP address dynamically. So I wrote simple script which gains my router IP and send me email:
```

#!/bin/bash

function send_mail {
	echo $1 | mutt -s "New IP" myemail.com
}

old_ip=

while true; do
	new_ip=`wget www.whatismyip.com/automation/n09230945.asp -O - -q`
	if [ -n "$new_ip" ] && [ "$new_ip" != "$old_ip" ];
	then
		old_ip=$new_ip
		send_mail "IP changed, sending new IP: $new_ip"
	fi
	sleep 5m	
done
```
I need it to run at system startup. When I'm adding it to .bash_profile **bash path/resolveIP &** I'm not getting any mail.
In case of **bash path/resolveIP** (without &) I'm getting mail, but I guess it will never get to the next command in .bash_profile.
So I put my script in /etc/init.d directory, but I don't know is it okay to have endless script there????

---

### Post by davidmohammed on 2010-08-07
can't help with the script.

However - I connect to a remote computer and like yours, the computer on the other end does not have a static IP address.

I use a server from no-ip.com.  It gives you a free DNS name that you can refer to from anywhere.

You can configure it in one of two ways 

1. use your router and see if it supports dynamic DNS - i.e. it will update no-ip.com automatically if the IP address changes.  

2. use the script from no-ip.com (download - linux).  it will automatically update no-ip.com when the computer IP address changes. 

I've then configured the router to forward VNC requests onto the remote computer.  When VNCing from my home PC, I use the new no-ip DNS name and it will resolve the IP address of the remote router.  The remote router will then forward the VNC request to the remote computer.

---

