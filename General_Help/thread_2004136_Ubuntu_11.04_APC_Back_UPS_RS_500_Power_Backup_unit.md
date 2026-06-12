---
title: "Ubuntu 11.04: APC Back UPS RS 500 Power Backup unit not working after upgrade?"
date: 2012-06-15
forum: General Help
---

### Post by Arborist222 on 2012-06-15
Hello, during my activity on pc using Ubuntu 11.04 we had a temporary loss of our local electricity supply and unusually the power backup unit failed maintain power to my pc.

I checked the UPS power storage information and unit was fully charged.

Recently I upgrading my pc system from Ubuntu 10.10 to Ubuntu 11.04?

Any helpful suggestions would be appreciated.

"Ubuntu is GREAT"

---

### Post by Zill on 2012-06-15
Arborist222:  I used to have a similar APC UPS but no longer use one for various reasons.  My recollection is that my UPS (and probably others) did *not* require a signal from the PC and/or OS to provide backup power as this was an automatic function of the UPS itself.  i.e.  When the AC power fails the unit *automatically* switches the load(s) over to the UPS battery/inverter supply.  In this scenario, the PC OS or software is irrelevant.

The software I used with my APC UPS was [apcupsd]("https://help.ubuntu.com/community/apcupsd") but this simply monitors the power status and then, if required, will shutdown the attached system(s) cleanly when the UPS battery power is about to expire.

So, to summarise, if your UPS failed to maintain power to the PC at all (i.e. when the outage occurred) then this looks like a fault *within* the UPS itself.  Alternatively, if the PC failed to shutdown properly after the outage started, then you may have a configuration problem with apcupsd.

---

