---
title: "Ubuntu didn't autoset for Daylight Savings Time"
date: 2011-03-17
forum: General Help
---

### Post by MasterNetra on 2011-03-17
Yea, Ubuntu didn't auto set for daylight savings...though to be fair a windows installation which is suppose to, didn't as well...Which I don't understand it. My system (ubuntu) is set to do it automatically... Neither has cable to think about it...but my atomic clock did.

---

### Post by pqwoerituytrueiwoq on 2011-03-18
mine adjusted just fine ubuntu lucid 10.04.2 and xubuntu 10.04.2
make sure your time zones are set right not everywere uses DST

---

### Post by MasterNetra on 2011-03-18
> **pqwoerituytrueiwoq said:**
> mine adjusted just fine ubuntu lucid 10.04.2 and xubuntu 10.04.2
make sure your time zones are set right not everywere uses DST

I did at install now its being stupid. I selected Detroit, MI as location now its just giving me EDT instead of EST. My area is supposed to do DST.

*Update*
Ended up just setting the time manually, don't understand why it didn't do it automatically but meh.

---

### Post by MasterNetra on 2011-03-18
Gah! It keeps reverting back to being a hour off...This is really starting to irritate me..

---

### Post by JKyleOKC on 2011-03-18
Open a terminal window and type "sudo ntpdate" to automatically update your clock settings from the same source your atomic clock uses.

You might get the same results by rebooting, since the boot sequence runs ntpdate automatically.

I installed the ntp (Network Time Protocol) daemon in my systems, to get the automatic update plus correction for drift of the hardware clock (which all boxes have, and all of them do drift a bit due to temperature changes). That keeps them all synchronized to the second at all times.

---

### Post by MasterNetra on 2011-03-18
> **JKyleOKC said:**
> Open a terminal window and type "sudo ntpdate" to automatically update your clock settings from the same source your atomic clock uses.

You might get the same results by rebooting, since the boot sequence runs ntpdate automatically.

I installed the ntp (Network Time Protocol) daemon in my systems, to get the automatic update plus correction for drift of the hardware clock (which all boxes have, and all of them do drift a bit due to temperature changes). That keeps them all synchronized to the second at all times.

I installed ntp, but when I ran sudo ntpupdate I got:
```

18 Mar 23:56:37 ntpdate[6607]: no servers can be used, exiting

```

---

### Post by AndrewX192 on 2011-03-19
> **MasterNetra said:**
> I installed ntp, but when I ran sudo ntpupdate I got:
```

18 Mar 23:56:37 ntpdate[6607]: no servers can be used, exiting

```

You need to specify a server to sync time from. Try "ntpdate pool.ntp.org" instead.

---

### Post by MasterNetra on 2011-03-19
> **AndrewX192 said:**
> You need to specify a server to sync time from. Try "ntpdate pool.ntp.org" instead.
```

19 Mar 00:15:48 ntpdate[2105]: the NTP socket is in use, exiting

```
It's like its fightin me on this all the way...

---

### Post by AndrewX192 on 2011-03-19
> **MasterNetra said:**
> ```

19 Mar 00:15:48 ntpdate[2105]: the NTP socket is in use, exiting

```
That means NTP is already running and managing your clock for you.
If you want to manually sync your clock, run:

"service ntp stop"
"ntpdate pool.ntp.org"
"service ntp start"

---

### Post by MasterNetra on 2011-03-19
> **AndrewX192 said:**
> That means NTP is already running and managing your clock for you.
If you want to manually sync your clock, run:

"service ntp stop"
"ntpdate pool.ntp.org"
"service ntp start"

It ran but no dice, I don't understand why it won't sync with DST in mind... I know it puts me at EDT instead of EST, and I put in Detroit and it even correctly set in the coordinates but it still wants to claim me at New York...stupid program...

---

### Post by AndrewX192 on 2011-03-19
> **MasterNetra said:**
> It ran but no dice, I don't understand why it won't sync with DST in mind... I know it puts me at EDT instead of EST, and I put in Detroit and it even correctly set in the coordinates but it still wants to claim me at New York...stupid program...
Is the time changing when you are using your computer normally, or does it only change on rebooting?

Please run "date && sudo hwclock -r" and post the output here.

This will show you the current time you have on your OS, followed by the time on your hardware clock.

---

### Post by MasterNetra on 2011-03-19
> **AndrewX192 said:**
> Is the time changing when you are using your computer normally, or does it only change on rebooting?

Please run "date && sudo hwclock -r" and post the output here.

This will show you the current time you have on your OS, followed by the time on your hardware clock.
```

Sat Mar 19 00:32:30 EDT 2011 
Sat 19 Mar 2011 04:32:46 AM EDT  -0.859389 seconds

```
*Wonders why his hardware clock is retarded*

---

### Post by AndrewX192 on 2011-03-19
> **MasterNetra said:**
> ```

Sat Mar 19 00:32:30 EDT 2011 
Sat 19 Mar 2011 04:32:46 AM EDT  -0.859389 seconds

```
*Wonders why his hardware clock is retarded*

There is nothing wrong there. Your hardware clock is actually set to UTC, which is recommended if you only have one operating system (usually Linux) installed. I will agree that it saying "EDT" for the hardware clock is confusing though.

It appears that your settings are correct. EDT should be what you are on (as per [http://wwp.greenwichmeantime.com/time-zone/usa/eastern-time/](http://wwp.greenwichmeantime.com/time-zone/usa/eastern-time/)).

---

### Post by JKyleOKC on 2011-03-19
Is the machine connected to the internet? I notice that your original message said "neither has cable" and if that means no internet connection, then ntp won't do anything for you and that's why neither machine auto-updated. They get the time-change signal via the internet.

If they are on line, though, take a look at your /etc/ntp.conf file and make certain that it has at least one line that begins "server" (it can have more than one). I've added two more to mine: ```
server ntp.tmc.edu
server wuarchive.wustl.edu
```Both are geographically closer to me than the default one...

EDIT: There's a totally different setting that tells the system whether to keep the "system clock" the same as the "hardware clock" and as AndrewX192 says, your hardware clock is just fine. The real problem is that for some reason it isn't properly synchronizing the system clock. Unfortunately I don't remember just where that "different setting" is located. Hopefully someone else will be able to follow this hint and get you fixed up again!

---

### Post by MasterNetra on 2011-03-19
> **JKyleOKC said:**
> Is the machine connected to the internet? I notice that your original message said "neither has cable" and if that means no internet connection, then ntp won't do anything for you and that's why neither machine auto-updated. They get the time-change signal via the internet.

If they are on line, though, take a look at your /etc/ntp.conf file and make certain that it has at least one line that begins "server" (it can have more than one). I've added two more to mine: ```
server ntp.tmc.edu
server wuarchive.wustl.edu
```Both are geographically closer to me than the default one...

EDIT: There's a totally different setting that tells the system whether to keep the "system clock" the same as the "hardware clock" and as AndrewX192 says, your hardware clock is just fine. The real problem is that for some reason it isn't properly synchronizing the system clock. Unfortunately I don't remember just where that "different setting" is located. Hopefully someone else will be able to follow this hint and get you fixed up again!

Yes, I am connected to the Internet via wireless. Also if EDT is indeed correct, then I guess for whatever reason it simply is not adjusting for DST...

---

### Post by JKyleOKC on 2011-03-19
I'm searching to find an answer for you, but so far all that I've found is a possible workaround.

Back in 2007, the US changed its DST changeover dates to add four weeks of daylight time, two at the start and two at the end. This made the conversion from UTC to DST inaccurate for all of those four weeks, until the timezone files on each system were updated to reflect the new changeover dates.

I would expect that your systems all have up to date timezone files, though. Nevertheless this is a workaround that was suggested at the time, to keep local times correct for the two weeks at each end:

"If a computer hasn't been updated with the new DST starting and ending dates, users may be tempted to manually set the clock to compensate. This won't be effective for very long if the computer is synchronizing its time to a time server, since the clock will soon revert back to the way it was. If the new DST rules can't be applied by a software update, a better work-around is to change the time zone setting, not the time. Choosing the time zone to your east will normally achieve the desired result and will remain correct even if your clock is being synchronized over the network. After the extended DST weeks are over, the time zone will need to be put back to the normal setting."

This may help; as it says, after the extended weeks are over, you would need to change back to the normal setting.

As for why it's saying "New York" when you're set for "Detroit" that's because the timezone file uses "New York" as its key for the Eastern time zone. If you do change your timezone, you can use any of them that indicate "UTC-4" as their offset.

Meanwhile I'll keep looking for that other setting. It's gotten under my skin!

---

### Post by MasterNetra on 2011-03-19
> **JKyleOKC said:**
> I'm searching to find an answer for you, but so far all that I've found is a possible workaround.

Back in 2007, the US changed its DST changeover dates to add four weeks of daylight time, two at the start and two at the end. This made the conversion from UTC to DST inaccurate for all of those four weeks, until the timezone files on each system were updated to reflect the new changeover dates.

I would expect that your systems all have up to date timezone files, though. Nevertheless this is a workaround that was suggested at the time, to keep local times correct for the two weeks at each end:

"If a computer hasn't been updated with the new DST starting and ending dates, users may be tempted to manually set the clock to compensate. This won't be effective for very long if the computer is synchronizing its time to a time server, since the clock will soon revert back to the way it was. If the new DST rules can't be applied by a software update, a better work-around is to change the time zone setting, not the time. Choosing the time zone to your east will normally achieve the desired result and will remain correct even if your clock is being synchronized over the network. After the extended DST weeks are over, the time zone will need to be put back to the normal setting."

This may help; as it says, after the extended weeks are over, you would need to change back to the normal setting.

As for why it's saying "New York" when you're set for "Detroit" that's because the timezone file uses "New York" as its key for the Eastern time zone. If you do change your timezone, you can use any of them that indicate "UTC-4" as their offset.

Meanwhile I'll keep looking for that other setting. It's gotten under my skin!

Actually I had to move it west to central.

---

### Post by JKyleOKC on 2011-03-19
Strange -- seems as if that would make it "Spring back, fall forward" instead of the real "forward, then back" changes, since we're at 3 p.m. when you're at 4...

---

### Post by MasterNetra on 2011-03-19
> **JKyleOKC said:**
> Strange -- seems as if that would make it "Spring back, fall forward" instead of the real "forward, then back" changes, since we're at 3 p.m. when you're at 4...

Going west would be going back, keep in mind the sun rises in the east and sets in the west. moving a hour west would delay the sun in reaching you. ergo going back a hour. Plus you can see this in time zone thing. Eastern time zone is GMT -5, while central is -6. Keeping in mind these are negative numbers.

At any rate, I guess sense its a server thing I guess there is nothing to do except that work around. Thread solved?

---

