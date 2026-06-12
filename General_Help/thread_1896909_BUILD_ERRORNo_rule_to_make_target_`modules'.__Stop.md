---
title: "BUILD ERROR:No rule to make target `modules'.  Stop."
date: 2011-12-18
forum: General Help
---

### Post by lordbux on 2011-12-18
I tried to compile something, in backtrack5r1 and had this following error

I understand that ubuntu is BT's Base this is why i am asking this here.

I have already install **linux-headers**
and also ran  build-prepare , ..etc

```

/root/Desktop/compat-wireless-3.2-rc1-1/config.mk:213: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.39.4/build M=/root/Desktop/compat-wireless-3.2-rc1-1 modules
make[1]: Entering directory `/lib/modules/2.6.39.4/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.39.4/build'
make: *** [modules] Error 2
```

any help will be greatly apriciated:guitar:

---

### Post by lordbux on 2011-12-19
> **lordbux said:**
> i tried to compile something, in backtrack5r1 and had this following error

i understand that ubuntu is bt's base this is why i am asking this here.

I have already install **linux-headers**
and also ran  build-prepare , ..etc

```

/root/desktop/compat-wireless-3.2-rc1-1/config.mk:213: "warning: Config_cfg80211_wext will be deactivated or not working because kernel was compiled with config_wireless_ext=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. With config_libipw=m."
make -c /lib/modules/2.6.39.4/build m=/root/desktop/compat-wireless-3.2-rc1-1 modules
make[1]: Entering directory `/lib/modules/2.6.39.4/build'
make[1]: *** no rule to make target `modules'.  Stop.
Make[1]: Leaving directory `/lib/modules/2.6.39.4/build'
make: *** [modules] error 2
```

any help will be greatly apriciated:guitar:

bump

---

### Post by lordbux on 2011-12-20
Solver it

ran the 2 commands written here

```

sudo apt-get install linux-headers-$(uname -r)


```

followed by

```
prepare-kernel-sources
cd /usr/src/linux
cp -rf include/generated/* include/linux/

```

---

### Post by ztMAMOHT on 2012-01-09
bash: cd: /usr/src/linux: No such file or directory

ls /usr/src/
linux-headers-3.0.0-14  linux-headers-3.0.0-14-generic

What I have to choose?

I'am try to compile driver for RTL8188CE and got error:
make[1]: Entering directory `/lib/modules/3.0.0-14-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-14-generic/build'
make: *** [all] Error 2
Have anyone any suggestions?

---

