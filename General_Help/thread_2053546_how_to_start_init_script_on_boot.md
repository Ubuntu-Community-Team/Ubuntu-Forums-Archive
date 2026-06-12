---
title: "how to start init script on boot"
date: 2012-09-05
forum: General Help
---

### Post by buffchick on 2012-09-05
hi, having an issue get a script to start on boot. It's in /etc/init.d. It works fine when called manually. i.e. ```
sudo service munge start/stop/restart
``` I tried adding it to default runlevels but it still won't start on boot. i.e. ```
sudo update-rc.d munge defaults
```

---

### Post by dozdozez on 2012-09-05
try:
```

sudo update-rc.d munge enable

```

and then ls -l /etc/rc2.d has to show a link to ../init.d/munge beginnig by S[number]

---

### Post by ajgreeny on 2012-09-05
You can also add the command minus the sudo to /etc/rc.local just above the final **exit 0** line

---

