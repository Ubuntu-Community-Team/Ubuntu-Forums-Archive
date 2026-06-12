---
title: "Suddenly init smashed, cron not working, services not starting, vpn odd ..."
date: 2010-10-25
forum: General Help
---

### Post by piccus on 2010-10-25
Hello,

I installed an LAMP Server on 10.10. Additionally a simple Sambaserver and a VPN is integrated.

Since 3 days I look at some strange behaviour:

```
sudo init 6
``` does not take effect. Nothing happens. ```
sudo reboot
``` is working, but all seems to be so ropy. It takes a significant while, before ssh-session is finally terminated.

After the system comes up again, the vpn-client gets not the same IP-address by DHCP-server, but the next following of dhcp-range. That is strange, because no other dhcp-client is busy. After a second reboot I get the correct first IP-address of the dhcp-range. That is reproducible.

cron is not working any more. None of my jobs is being triggered. Nothing is logged in /var/log/syslog any more.

Services (apache2, mysql, smbd) are not running at the start. I have to run them up manually.

Seems like init is somehow smashed?

What is your guess? What futher information do I have to provide for analysis?

Thank you friends!
piccus

---

### Post by dcstar on 2010-10-25
> **piccus said:**
> Hello,

I installed an LAMP Server on 10.10. Additionally a simple Sambaserver and a VPN is integrated.

Since 3 days I look at some strange behaviour:
...........
What is your guess? What futher information do I have to provide for analysis?


What do **you **see in the var/log/syslog file?

---

### Post by piccus on 2010-10-25
Thank you for helping me out!

I traced back my actions and found the script I should not have edited.

---

