---
title: "Restoring Hibernate in 12.04 Precise Pangolin"
date: 2012-06-12
forum: General Help
---

### Post by Ralph L on 2012-06-12
Thought an extra posting of how to restore hibernation might be useful, since I had trouble finding it.

[http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html) 

Open Terminal and enter following command:
sudo gedit /var/lib/polkit-1/localauthority/50-local.d/hibernate.pkla 
copy and paste the following code in file:
[Re-enable Hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
Restart to see hibernate option.

---

