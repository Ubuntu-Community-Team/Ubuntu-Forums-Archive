---
title: "wlan0 not comming up at boot"
date: 2006-04-05
forum: General Help
---

### Post by nin881 on 2006-04-05
When I boot my Wlan0 doesn't come up until i manually run **sudo ifup wlan0 **in bash. what can I do to get it to start so it will come up when eth0 comes up.

Thank you,
Tom

---

### Post by karthik085 on 2006-04-05
If you are not using ndiswrapper, you can configure network interfaces by editing the file: /etc/network/interfaces or Networking (System->Administration).
If you are using ndiswrapper, add ndiswrapper to /etc/modules

[QUOTE=nin881]When I boot my Wlan0 doesn't come up until i manually run **sudo ifup wlan0 **in bash. what can I do to get it to start so it will come up when eth0 comes up.

Thank you,
Tom[/QUOTE]

---

### Post by Darkriser on 2006-04-05
try adding "auto wlan0" to your /etc/network/interfaces file

---

### Post by nin881 on 2006-04-05
The module already loads at boot, but interface doesn't come up automatically. I'll change interfaces file when I get home.

Thanks,
Tom

---

### Post by nin881 on 2006-04-05
Thanks guys, I got her to load without intervention.

You where a big help!

Tom

---

