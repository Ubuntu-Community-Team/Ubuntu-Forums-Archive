---
title: "Is there a seasonal time change option in Ubuntu?"
date: 2009-08-04
forum: General Help
---

### Post by oxf on 2009-08-04
Is there a option to turn on/off how the system clock adjusts itself by one hour to take account of summer or daylight savings time?

 There is in windows and I assume there is in Ubuntu as well somewhere. I Just cant see it anywhere, eg System>Administration>Time and Date. 

Thanks!

---

### Post by llamabr on 2009-08-04
Have you tried running:

```
sudo dpkg-reconfigure tzdata
```

---

### Post by oxf on 2009-08-04
> **llamabr said:**
> Have you tried running:

```
sudo dpkg-reconfigure tzdata
```

No I haven't, what does this do? I was assuming there would be an option in the GUI somewhere that I'd missed. Not that I'm opposed to doing via Terminal though:)

---

### Post by LowSky on 2009-08-04
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by llamabr on 2009-08-04
I just looked, and it didn't work.

There are some places that don't have daylight savings time.  You could set yours with the TZ option, and then manually add or subtract.  Looks like BRT doesn't have daylight savings.  What time zone are you in?

---

### Post by oxf on 2009-08-04
> **llamabr said:**
> I just looked, and it didn't work.

There are some places that don't have daylight savings time.  You could set yours with the TZ option, and then manually add or subtract.  Looks like BRT doesn't have daylight savings.  What time zone are you in?

Well I'm in the UK which is GMT (UTC) +1 right now. That doesnt seem to give me an automatic seasonal adjustment from what I can see

---

### Post by martinbaselier on 2009-08-04
Do you use UTC and network timeservers? (NTP)

**cat /etc/default/rcS | grep UTC**

To change it:
sudo gedit /etc/default/rcS
and change UTC=no to UTC=yes

This will affect your windows time to. There's a fix described in the above link.

I had to enable that to make DST work on my machine. 

If you use NTP, I think it will show immediately when restarting ntp:

**sudo service ntp restart**

---

### Post by oxf on 2009-08-04
> **martinbaselier said:**
> Do you use UTC and network timeservers? (NTP)

**cat /etc/default/rcS | grep UTC**

To change it:
sudo gedit /etc/default/rcS
and change UTC=no to UTC=yes

This will affect your windows time to. There's a fix described in the above link.

I had to enable that to make DST work on my machine. 

If you use NTP, I think it will show immediately when restarting ntp:

**sudo service ntp restart**

Thank you for that! Thats most useful and answers some other questions I had. 
Part of my problem was that I was expecting Linux to have the same sort of DST setting option as Windows.  One more thing to learn :)

---

