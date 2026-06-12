---
title: "monitor resolution"
date: 2009-11-24
forum: General Help
---

### Post by Shubhang on 2009-11-24
Please HELP. Am new to this. I installed ubuntu 9.10, but the monitor is shown is default and i can not change its resolution. how do i change the default resolution of my default monitor from 800X600 from to something more. Thanks

---

### Post by grandtoubab on 2009-11-24
Start in recovery mode to reconfigure your /etc/X11/xorg.conf file.
select user root shell

(write the following command  on paper and be careful of capital X)

```
X -configure
```



```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```



```
reboot
```

---

