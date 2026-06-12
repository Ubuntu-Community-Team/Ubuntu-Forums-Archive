---
title: "Restarting service on boot"
date: 2012-05-11
forum: General Help
---

### Post by aristosv on 2012-05-11
I have installed OpenVPN-ALS on an Ubuntu machine.
For some reason, after Ubuntu starts, I have to restart the "Adito" service in /etc/init.d, otherwise OpenVPN-ALS will tell me that I have the wrong credentials on login.
 
So every time Ubuntu starts, I run:
 
```
 
sudo /etc/init.d/adito stop
sudo /etc/init.d/adito start

```
 
and I can login on OpenVPN-ALS just fine.
 
So how can I automate the process of restarting the adito service?
 
Thanks

---

