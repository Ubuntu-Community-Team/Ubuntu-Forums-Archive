---
title: "Firefox stalls loading Squirrelmail website"
date: 2010-10-28
forum: General Help
---

### Post by jcerovac on 2010-10-28
The basics: Ubuntu 10.04 Lucid x64 with Firefox 3.6.11 on a Thinkpad T61p 2gb ram/500gb HD.

When I try to access my email via Squirrelmail, Firefox hangs on loading. If I stop the page from loading, wait a few minutes, then try again, I have a 50:50 chance of it loading this time.

I've run the update to make sure I have the most recent versions of software, but it still hangs. I've tried a few cursory searches, but find nothing referencing Lucid or that is otherwise current.

Thanks all for the assist!

Jace

---

### Post by lovinglinux on 2010-10-29
Disable ipv6. See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by jcerovac on 2010-10-29
> **lovinglinux said:**
> Disable ipv6. See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

This is a good list, I'll bookmark it. I tried the update for IPv6, but to no avail. Restarted Firefox with no change; tried a reboot, too - but same difference.

This symptom is only on a https connection with Squirrelmail, all other websites are fine.

Jace

---

### Post by lovinglinux on 2010-10-29
> **jcerovac said:**
> This is a good list, I'll bookmark it. I tried the update for IPv6, but to no avail. Restarted Firefox with no change; tried a reboot, too - but same difference.

This symptom is only on a https connection with Squirrelmail, all other websites are fine.

Jace

Try a different DNS server like OpenDNS or Google DNS. But first, try to reach the site via IP number. If it works, then is a DNS issue.

---

