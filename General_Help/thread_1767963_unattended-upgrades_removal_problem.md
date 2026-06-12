---
title: "unattended-upgrades removal problem"
date: 2011-05-26
forum: General Help
---

### Post by okhowaboutthisusername on 2011-05-26
9.04 server

Yesterday, I removed the unattended-upgrades package. Today, cron sent me a msg:
/etc/cron.daily/apt: line 244: unattended-upgrade: command not found

Looking at the apt script, I can see a lot of other stuff aside from unattended-upgrades. I don't think I should simply delete the script, but I'm also unsure of which parts to remove/comment.

---

