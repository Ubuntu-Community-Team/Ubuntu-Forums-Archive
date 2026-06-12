---
title: "Startup script not running on startup"
date: 2010-08-16
forum: General Help
---

### Post by wynand2020 on 2010-08-16
HI

I have a script in the init.d folder on ubuntu which needs to run on startup, the problem is I doesn't run because of permission problems.

I have done all the below but still it doesnt run;

sudo cp [name].sh /etc/init.d
sudo chmod +x /etc/init.d/[name].sh
sudo update-rc.d [name].sh defaults


Here is my script, please help!!! I think its a permission issue?!?


#!/bin/sh

sleep 10

# Check if root

if [ "$(whoami)" != "root" ]; then
echo "Not running as root. Exiting..."
exit 0
else
echo "Running as root. Good"
fi


cd /usr/sbin/bearerbox -v 1 /etc/kannel/kannel.conf
cd /usr/sbin/smsbox -v 1 /etc/kannel/kannel.conf

---

