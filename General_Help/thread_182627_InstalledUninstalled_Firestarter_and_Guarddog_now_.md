---
title: "Installed/Uninstalled Firestarter and Guarddog now cant connect to network"
date: 2006-05-26
forum: General Help
---

### Post by Protege on 2006-05-26
I recently installed firestarter, tested it, and uninstalled it. Then I did the same with guarddog. So now both are uninstalled using sudo apt-get remove. 

1. On boot I see guarddog is starting up on the ubuntu boot screen prior to the login page appearing. It seems to start up fine, but shouldn't it be gone since I uninstalled it?

2. Also on the boot when it tries to configure network devices it hangs unless I press crtl+c to skip it. Then when I am logged in i cant get on the Internet or my LAN. I have reset the iptables with iptables -F and iptables -X and still no connection.

Everything was working fine until I installed/uninstalled firestarter and guarddog. Please if anyone can help I really would like to get my server up and running again as soon as I can.

---

### Post by cskeide on 2006-05-26
Did you restart networking after flushing iptables?
```

sudo /etc/init.d/firestarter stop
sudo /etc/init.d/guarddog stop
sudo iptables -F
sudo dpkg -P firestarter guarddog
sudo /etc/init.d/networking restart

```

---

### Post by Protege on 2006-05-26
[QUOTE=cskeide]Did you restart networking after flushing iptables?
```

sudo /etc/init.d/firestarter stop
sudo /etc/init.d/guarddog stop
sudo iptables -F
sudo dpkg -P firestarter guarddog
sudo /etc/init.d/networking restart

```[/QUOTE]

That did it! Thank you so much that was so frustrating to deal with. I really like firestarter but it kept blocking my LAN. I tried to put an exception in the policy for 192.168.1.1/24 for my LAN but it still blocked it. I am just happy to have it functioning again. Thanks again and long live Ubuntu!

---

