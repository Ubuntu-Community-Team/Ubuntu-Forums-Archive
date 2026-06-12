---
title: "Inhibit sleep/suspend when vpn is on"
date: 2012-03-07
forum: General Help
---

### Post by suikula on 2012-03-07
Hi

I have server (ubuntu 11.04) which I use only via ssh. I use this server to tunnel vpn to my work network. Now I want little script that inhibits sleep/suspend while my vpn is on. So I made this this script and I run it in cron.

```

#!/bin/bash
VPN=`/sbin/ifconfig | grep tun0`
PREVENTSLEEP='/usr/bin/gnome-screensaver-command --poke'
if [ "${VPN}" != "" ];
then
	echo "vpn on"
	gconftool-2 --set /apps/gnome-power-manager/actions/sleep_type_ac --type string "nothing"
	gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0 
        $PREVENTSLEEP

else
	echo "vpn off"
	gconftool-2 --set /apps/gnome-power-manager/actions/sleep_type_ac --type string "suspend"
	gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 7200
fi

```

My idle time to sleep is 2 hours and every time after 2 hours this machine goes to sleep. What is the proper way to accomplish this ?
Right answer is not "turn of sleep" cause I need it when vpn tunnel is not on.

Thanks for any suggestions

---

