---
title: "time change not being reflected...maybe im wrong"
date: 2010-11-07
forum: General Help
---

### Post by inspiteofmyself on 2010-11-07
i have never had an issue with this before... but i am with 10.10

hardware clock is set to UTC. my timezone is set to America/Chicago (central time). when the time change occurred tonight, the clock just sat there giggling at me. i synced time with a missouri server, same thing... corrected by a second or two, and did do anything more.

it was supposed to jump back 1 hour, but it did not do it. 

```

fluid@fluid-desktop:~$ date
Sun Nov  7 03:00:01 CST 2010

fluid@fluid-desktop:~$ zdump -v /etc/localtime | grep 2010
/etc/localtime  Sun Mar 14 07:59:59 2010 UTC = Sun Mar 14 01:59:59 2010 CST isdst=0 gmtoff=-21600
/etc/localtime  Sun Mar 14 08:00:00 2010 UTC = Sun Mar 14 03:00:00 2010 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  7 06:59:59 2010 UTC = Sun Nov  7 01:59:59 2010 CDT isdst=1 gmtoff=-18000
/etc/localtime  Sun Nov  7 07:00:00 2010 UTC = Sun Nov  7 01:00:00 2010 CST isdst=0 gmtoff=-21600

```

it should be 2am up there, not 3am... and the data looks ok to me... what am i missing here?

---

### Post by geoffmcc on 2010-11-07
I thought time change was happening too. Only way i knew was cause someone mentioned on facebook. All my clocks are computers or cableboxs

anyways mine didn't change either (to the best of my knowledge) so i figured its 2am tonight, but either way i am kinda confused as to what time it really is.

---

### Post by inspiteofmyself on 2010-11-07
> **geoffmcc said:**
> I thought time change was happening too. Only way i knew was cause someone mentioned on facebook. All my clocks are computers or cableboxs

anyways mine didn't change either (to the best of my knowledge) so i figured its 2am tonight, but either way i am kinda confused as to what time it really is.

lol... we will wander clueless for days im sure.

---

### Post by geoffmcc on 2010-11-07
time change + a week of insomnia = very confused 

But it did happen.


Also, it 4:34 EST now and your initial post was 33 minutes ago - so at that time it was 3am - you should be good

---

### Post by robert shearer on 2010-11-07
What happens if you reboot ?.

---

### Post by inspiteofmyself on 2010-11-07
> **robert shearer said:**
> What happens if you reboot ?.

tried it...and nothing happened. it is still incorrect. :(

ive tried disabling the ntp service, and using ntpdate to update the time as well...still an hour off.

---

### Post by geoffmcc on 2010-11-07
It should be going on 4am now CST - your first post said it was 3am. I think your clock is right.

---

### Post by cracker89 on 2010-11-07
I had that problem too. Even though I am in India. There is some issue with this perhaps. Just set it to your time manually and then try updating from a server. I have disconnected server support to it and kept it manually. It seems to work fine then.. .

---

### Post by inspiteofmyself on 2010-11-07
just got on the computer today, and it has corrected itself... i have no idea why it was not correct last night, but it was not correct... we verified it with every other "online" device in the house and with friends, and this computer was the only thing that was "off".

it is correct now though.

---

