---
title: "How to change the timezone permanently?"
date: 2010-01-03
forum: General Help
---

### Post by Rigbonn on 2010-01-03
So, here's my problem. Every time I'm trying to change my timezone, it last until I'm restarting my comp again, it seems like it doesn't save the changes permanently.
I'm using Ubuntu v9.10 installed through Wubi. My timezone is set currently via BIOS.

What should I do?

---

### Post by Rigbonn on 2010-01-06
I still have this problem.

---

### Post by Leppie on 2010-01-06
i believe you have to install the ntpdate (network time protocol) client.
```
sudo apt-get install ntpdate
```

---

### Post by warfacegod on 2010-01-06
I assume you modified your BIOS setting.

Go to Right click your clock> Preferences> Location tab> select add> type a location name> use the drag down menu to select a new time zone.

---

### Post by rnerwein on 2010-01-06
hi - be lucky to use ubuntu
what you need is:
apt-get install tzdata
and run then
dpkg-reconfigure tzdata

an to play whith timezones (no change is made) use 
tzselect
ciao

---

### Post by philinux on 2010-01-06
tzdata is already installed by default.

---

### Post by Skip Da Shu on 2010-03-26
I still can't seem to get it set for India, GMT-5.5

Skip

PS: Using UNR v9.10

---

### Post by gmargo on 2010-03-27
> **Skip Da Shu said:**
> I still can't seem to get it set for India, GMT-5.5


Probably you mean GMT+5.5, not minus.
Try setting the timezone to 'Asia/Kolkata' which is UTC/GMT +5:30 hours.

```

$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Asia/Kolkata'
Local time is now:      Sat Mar 27 18:50:18 IST 2010.
Universal Time is now:  Sat Mar 27 13:20:18 UTC 2010.

```

---

### Post by Skip Da Shu on 2010-03-28
> **gmargo said:**
> Probably you mean GMT+5.5, not minus.
Try setting the timezone to 'Asia/Kolkata' which is UTC/GMT +5:30 hours.

```

$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Asia/Kolkata'
Local time is now:      Sat Mar 27 18:50:18 IST 2010.
Universal Time is now:  Sat Mar 27 13:20:18 UTC 2010.

```

Yes, U r right... GMT + 5.:30.. and yes, this worked.  Thanx much.

Skip

---

