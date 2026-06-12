---
title: "Clock issues // NTP"
date: 2009-11-29
forum: General Help
---

### Post by Ezzi on 2009-11-29
i cant seem to keep my NTP date updated i have NTP running but sometimes i have to 

```
 /etc/init.d/ntp stop
```

then 

```
ntpdate ntp.ubuntu.com
```

then 

```
/etc/init.d/ntp start
```

just to keep my clock updated

---

### Post by leorolla on 2009-12-02
Thanks for the hint!

I have uninstalled ntp.

```
sudo apt-get remove ntp

```
Warning: You are removing a package!
It does not come with Ubuntu 9.10. Maybe you have installed it yourself or you have another distro. Do it at your risk.

Now ntpdate works as you say... (without the start-stop headache)

They teach how you can get ntpdate running automtically every day at:
[https://help.ubuntu.com/9.10/serverguide/C/NTP.html](https://help.ubuntu.com/9.10/serverguide/C/NTP.html)

Anyway, now my "ntp" seems to be running well, after I added "ntp" to the server list.

---

