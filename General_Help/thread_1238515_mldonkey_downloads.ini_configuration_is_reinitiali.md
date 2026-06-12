---
title: "mldonkey downloads.ini configuration is reinitialized on reboot."
date: 2009-08-12
forum: General Help
---

### Post by Coume on 2009-08-12
Hello,

I just install 9.04 on a new workstation to test it out as I have been a Arch user for a while now.

I installed mldonkey and want to edit the /var/lib/mldonkey/downloads.ini file to allow remote connection within my network by editing the **allowed_ips = [ "127.0.0.1"; "192.168.1.102"]** range.

To edit it, I simply type: **sudo nano /var/lib/mldonkey/downloads.ini  **and save it...

I then reboot to have the change take effects but the downloads.ini is like reinitialized to it default value...

Do you know what I am missing there? I cannot see what I am doing wrong :(

Thanks in advance for your help.
Ludo

---

### Post by kinkarsaha on 2010-07-22
You have missed to "STOP" the daemon service, before you edited the Downloads.ini

You can Start & STOP the mldonkey daemon service by the following way :

```
sudo /etc/init.d/mldonkey-server start
``````
sudo /etc/init.d/mldonkey-server stop
```Then edit the ini and restart the daemon.

Hope this helps.

---

