---
title: "NTP continuously getting out of whack?"
date: 2012-07-17
forum: General Help
---

### Post by Roasted on 2012-07-17
I didn't notice how much of a problem NTP was on my server (12.04) until I began running OwnCloud on it. The sync client for OwnCloud requires that the time be meshed up within a 10 second window. Several times now in the 30-40 days I've been running OwnCloud it's gone out of whack, requiring me to SSH in and ntpdate ntp.ubuntu.com.

I've never had to do this before. Of course I could cron it to run daily, but I'm not sure that really "fixes" the issue. Time/date settings are set to automatic (New York). Any way I can get a more permanent fix in?

---

### Post by dodo3773 on 2012-07-18
Ntp should already provide a daemon. Seems like a cron job would be a little redundant. There are ways to debug ntpd though. Pretty sure you can debug it with something like "sudo ntpd -qgddd" (the -q switch is to update (ntpupdate is depreciated / not needed any more)). 

Also, ntpd may expect you to have a /etc/services file with an ntp service defined in it (if you get an error from the previous command similar to "Error : Servname not supported for ai_socktype" then that may be the issue). Here is the relevant section from mine if it helps at all:
```

$ grep "^ntp" /etc/services
ntp             123/tcp    # Network Time Protocol
ntp             123/udp    # Network Time Protocol

```

---

