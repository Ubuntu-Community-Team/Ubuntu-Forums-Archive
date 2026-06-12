---
title: "Hot to automatically start lsyncd daemon on server reboot"
date: 2011-06-14
forum: General Help
---

### Post by dean.p on 2011-06-14
My problem now is that lsyncd does not automatically start if  the server reboots. I need lsyncd to start automatically also using the  --delay 5 option.

I've had trouble finding any info on this other that some Japanese sites  (I cant read japanese) using chkconfig, although it didn't work as I think  chkconfig is depreciated anyway.

I'm sing Ubuntu server 10.10, any help would be appreciated.... I'm not a linux guru but get by with the basics

---

### Post by sanguinoso on 2011-06-14
You can put your command in the /etc/rc.local file to make it start on boot.

---

### Post by btindie on 2011-06-14
If there isn't one for it already, you can create your own init script that will start it at boot up. Either using the older System-V style init scripts in /etc/init.d or the newer upstart script in /etc/init.

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by dean.p on 2011-06-15
Thanks, I'll try the easier option for now suggested by sanguinoso :)

Thanks.

---

