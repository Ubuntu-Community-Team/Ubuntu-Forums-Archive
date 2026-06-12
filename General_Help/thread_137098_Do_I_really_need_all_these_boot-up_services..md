---
title: "Do I really need all these boot-up services."
date: 2006-02-27
forum: General Help
---

### Post by bb002 on 2006-02-27
My system doesn't have a printer and it isn't likely going to change. I don't have any HP products. I have no use for VLM either. Would it be ok for me to uninstall these items? or atleast remove them from the boot scripts.

HP Imaging and something or other (??)
Cups printing deamon (cupsys)
Enterprise Volume Managment Services  (evms)

There are proably more services I doubt I need but I'm not at my machine to take a look. I've tried using BUM but it refuses to let me disable anything on the "Startup and shutdown scripts" tab and everything I want disabled happens to BE on that tab.

---

### Post by Xian on 2006-02-27
[QUOTE=bb002]I've tried using BUM but it refuses to let me disable anything on the "Startup and shutdown scripts" tab and everything I want disabled happens to BE on that tab.[/QUOTE]

Install and use sysv-rc-conf. That should give you access.

---

### Post by bb002 on 2006-02-27
Cool I'll try it out to night.

---

### Post by bb002 on 2006-02-27
Cool that worked! Couple questions though.

1) what's vebsave, adt, and rmnologin?
2) I've completely disabled blootooth but it still goes by during startup.


Seems the services I mentioned before eat up about 100MB of RAM!? I have 1GB of RAM and on a fresh boot my system always had about 40% RAM in use. Now it is only 31%. I even rebooted a couple times just to make sure.

---

### Post by Ndlovu on 2006-02-27
You might find this post useful: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) (HowTo: Speed up ubuntu boot process - the way you can feel it.)

Most of the startup processes are explained in fairly decent detail. I used it to simplify my boot process a great deal.

---

