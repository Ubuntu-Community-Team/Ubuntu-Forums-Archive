---
title: "Keeping time to EST??"
date: 2011-03-23
forum: General Help
---

### Post by pk_naptown on 2011-03-23
I have a Ubuntu 10.04 box that I want to keep on Eastern Standard Time. 

Under the Time & Date GUI I select the correct time zone, put it in Manual mode, set the time and it is fine until I reboot. Then the clock advances one hour about 20 seconds after boot.

I don't remember this happening a month ago before DST started.

Does anyone know of a way to keep the beast on EST, not EDT?

Thanks for your help!

---

### Post by gmargo on 2011-03-23
You need to configure your timezone as **SystemV/EST5** or as **Etc/GMT+5**.

However, you cannot do so from the Gnome GUI (it does not include the SystemV or Etc timezone options).  You must use the command line and run:
```

sudo dpkg-reconfigure tzdata

```and navigate the timezone selection menu to SystemV and then select EST5 (or Etc then GMT+5). SystemV/EST5 is preferable since the 'date' output will show EST not GMT+5.

```

$ sudo dpkg-reconfigure tzdata

Current default time zone: 'SystemV/EST5'
Local time is now:      Wed Mar 23 13:14:50 EST 2011.
Universal Time is now:  Wed Mar 23 18:14:50 UTC 2011.

```

---

### Post by pk_naptown on 2011-03-24
Thanks for the help gmargo! It works fine now.

---

