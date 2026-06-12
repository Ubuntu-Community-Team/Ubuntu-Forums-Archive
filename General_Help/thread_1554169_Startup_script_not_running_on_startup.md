---
title: "Startup script not running on startup"
date: 2010-08-16
forum: General Help
---

### Post by wynand2020 on 2010-08-16
Hi

I'm trying to run a script at startup, but it fails.

I have tried all of the following but still no luck:

sudo cp [name].sh /etc/init.d
sudo chmod +x /etc/init.d/[name].
shsudo update-rc.d [name].sh defaults

Here is my script, I think it has a problem with permissions, please please help!!!

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

### Post by Smart Viking on 2010-08-16
Well obviously your not running it as root? It is in your script, if not root, exit. :)

---

### Post by wynand2020 on 2010-08-17
But how do i then run it as root?

where do i add it in the script?

---

