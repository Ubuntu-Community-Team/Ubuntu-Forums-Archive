---
title: "Changing time options"
date: 2010-03-15
forum: General Help
---

### Post by AudioDef on 2010-03-15
I'm using Xubuntu. I want to tell my system to ignore "daylight savings time". I have for now manually corrected the time, but I'd like to know how to do this so my system stays on EST and never changes to anything else.

---

### Post by dcstar on 2010-03-16
> **AudioDef said:**
> I'm using Xubuntu. I want to tell my system to ignore "daylight savings time". I have for now manually corrected the time, but I'd like to know how to do this so my system stays on EST and never changes to anything else.
```

sudo tzselect
```

---

### Post by AudioDef on 2010-03-16
Thanks!

---

### Post by AudioDef on 2010-03-17
No, that actually didn't work after all. Next reboot, the system is back to EDT. I need to change the time permanently.

---

### Post by gmargo on 2010-03-17
Please say why you want to ignore Daylight Savings Time.  Are you in a location that normally does not have DST, or is this just a whim?  If the former, then "dpkg-reconfigure tzdata" and select the proper time zone.  If the latter....?

---

### Post by dcstar on 2010-03-17
> **AudioDef said:**
> No, that actually didn't work after all. Next reboot, the system is back to EDT. I need to change the time permanently.

There are multiple areas where timezone (and locale) settings can be set, some seem to affect the base system and others the individual user accounts, here a some of them:

```
/etc/timezone
/etc/default/rcS
```

I also now see that the tzselect man page says you should use the dkpg-reconfigure command instead!

---

### Post by AudioDef on 2010-03-18
I used the dkpg-reconfigure command this time. Thanks! We'll see if it sticks on the next reboot.

---

### Post by AudioDef on 2010-03-19
OK, that also did not work. I did find out about hwclock: [http://manpages.ubuntu.com/manpages/jaunty/man8/hwclock.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/hwclock.8.html)

This is probably what I want. I've set the hwclock and I'll know on the next reboot if this is the solution. 

Ubuntu does not seem very user-friendly to those of us who are more technical and know what we want in detail. :evil:

---

### Post by AudioDef on 2010-03-22
I appreciate everyone's response so far. None of these suggestions have worked, however. On every boot, my system is still kow-towing to daylight savings. 

Does anyone have any other suggestions?

I'm considering leaving Ubuntu for Gentoo, as Ubuntu seems to be fundamentally flawed in that it will not cooperate with users on very basic operations. :confused:

---

### Post by gmargo on 2010-03-22
To keep EST without Daylight Savings Time you need to use one of the SystemV timezones.  Run "dpkg-reconfigure tzdata", and go down the menu to "SystemV", select it, and then select "EST5".

```

$ date ; date -u
Mon Mar 22 08:43:39 PDT 2010
Mon Mar 22 15:43:39 UTC 2010
$ sudo dpkg-reconfigure tzdata

Current default time zone: 'SystemV/EST5'
Local time is now:      Mon Mar 22 10:44:12 EST 2010.
Universal Time is now:  Mon Mar 22 15:44:12 UTC 2010.

$ date ; date -u
Mon Mar 22 10:44:16 EST 2010
Mon Mar 22 15:44:16 UTC 2010



```

---

### Post by AudioDef on 2010-03-23
Thanks! This suggestion is the one that makes the most sense. 

Why does Ubuntu make this so complicated and vague? Every other OS I've ever used I can simply set the system and hwclocks and it stays there.

---

