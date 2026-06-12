---
title: "Lightweight NTP client?"
date: 2010-06-29
forum: General Help
---

### Post by littlebigman on 2010-06-29
Hello

I'd like to run NTP to sync an [ARM-based appliance]("http://en.wikipedia.org/wiki/SheevaPlug"). Since NAND memory is scarce, I was wondering it there is a lighter alternative to the NTP package?

```

# apt-get install ntp
[...]
After this operation, 29.7MB of additional disk space will be used.

```

BTW, what is the right way to sync a single host with NTP servers on the Net? I was thinkind of running ntpdate nightly with CRON.

[LIST]
[*]ntpdate: Update the date/time immediately

[*]nt???: Update the date/time progressively

[*]ntpd: NTP server to let local hosts sync with it instead of each connecting to NTP servers on the Net
[/LIST]

Thank you.

---

### Post by tgalati4 on 2010-06-29
If you have one ntp server on your LAN broadcasting a time packet, then other linux machines will pick up the time without ntpd running.  This method would work in a factory but not for a consumer device.  I've got ntpd running on my nokia n800, so it can't be that heavy.

I just checked, it's 176 kb and called openntpd based on openbsd port to ARM.

---

