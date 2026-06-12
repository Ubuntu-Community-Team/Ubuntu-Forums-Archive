---
title: "Start service as another user"
date: 2006-04-13
forum: General Help
---

### Post by Linux-Newbe on 2006-04-13
I am trying to install zabbix and am at the stage where i need to start  Zabbix_server as zabbix user. But can not seem to use sudo to do this. Can any one please help

---

### Post by nemequ on 2006-04-13
```
su -u zabbix
``` where zabbix is the username you want to switch to. Then you can run whatever commands you want--to log out, use exit.

---

