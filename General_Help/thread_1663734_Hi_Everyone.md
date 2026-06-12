---
title: "Hi Everyone"
date: 2011-01-10
forum: General Help
---

### Post by ih8bugz on 2011-01-10
I am new to all things linux. I recently downloaded ubuntu 10.10 gnome. I am using a toshiba satellite a105-s4004, with a matshita uj-841s cd/dvd drive. I am unable to use my cd/dvd since loading ubuntu. The smart status on the disk utility reads "not supported". Can anyone let me know how to fix it?

---

### Post by oopsie on 2011-01-10
I did some searching, but can't find anything anywhere sorry. It may just not be supported. Though if anyone more experienced with linux turns up who knows better, I'll gladly admit I'm no expert.

---

### Post by prshah on 2011-01-10
> **ih8bugz said:**
> I am unable to use my cd/dvd since loading ubuntu. The smart status on the disk utility reads "not supported". 

SMART does not work for optical or other drives (except for internal HDDs SATA/IDE). This is not an error; this is the expected result.

What happens when you try to use the CD/DVD drive? According to the specs for your machine, it has a DVD-RAM drive, which should be supported out-of-the-box in Ubuntu.

Please post back some debugging info: put in a CD/DVD, open a terminal (Applications-Accessories-Terminal) and give the commands```
dmesg|grep -i dvd
sleep 5 && tail /var/log/messages
``` and post back the output here.

---

