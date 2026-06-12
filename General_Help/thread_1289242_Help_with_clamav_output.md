---
title: "Help with clamav output"
date: 2009-10-12
forum: General Help
---

### Post by CharlesA on 2009-10-12
Hi all,

I scheduled clamav to run a scan at midnight. I checked the "mail" that I got from cron and this is what was there:

```

From: root@thor.sd.cox.net (Cron Daemon)
To: charles@thor.sd.cox.net
Subject: Cron <charles@thor> clamscan -rvi / | mail email@root
Date: Mon, 12 Oct 2009 00:30:43 -0700

**LibClamAV Error: cli_readn: read error: Invalid argument**
LibClamAV Error: cli_readn: read error: Invalid argument
LibClamAV Error: cli_readn: read error: Invalid argument
**LibClamAV Error: cli_readn: read error: Operation not supported**
LibClamAV Error: cli_readn: read error: Invalid argument
LibClamAV Error: cli_readn: read error: Operation not supported
**LibClamAV Error: cli_readn: read error: Function not implemented << 170 of these**

```

I'm not quite sure what the deal is. I saw some stuff online that these happen when it tries to scan files in the /sys, /dev and /proc directories.

Anyhow, I was wondering if anyone has run into these errors before and knows what causes them.

---

