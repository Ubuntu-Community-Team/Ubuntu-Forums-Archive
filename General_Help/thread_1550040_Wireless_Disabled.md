---
title: "Wireless Disabled"
date: 2010-08-10
forum: General Help
---

### Post by borth92 on 2010-08-10
I was using my laptop like normal and the wireless went out. when i click the wireless in the notification area it says wireless disabled. I've fixed this same problem before on other computers but cannot find the same solution as before online. I know theres some file I have to edit that got changed to wireless_enabled=false
but i cannot remember what file to edit...please help

---

### Post by borth92 on 2010-08-10
found the old link. here is how to fix it when wireless is disabled and not clickable.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/599431](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/599431)

however this time, on restart the file reverts to: enablewireless=false...

Anyone have an idea?

---

### Post by borth92 on 2010-08-10
Updating to 10.10 Maverick to see if ubuntu has resolved this issue int he new alpha release...but it would be nice if i could get a little feedback....

---

### Post by rend on 2010-08-10
This works for me.

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

---

