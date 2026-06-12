---
title: "Update Manager Full Auto?"
date: 2011-11-16
forum: General Help
---

### Post by jim_deadlock on 2011-11-16
I'm converting my dad to Ubuntu and want to make it as simple for him as possible, so I was wondering if there's a way to make the Update Manager install everything in the background without ever showing itself?

---

### Post by Slim Odds on 2011-11-16
You could create a cron job that runs "apt-get update && apt-get --yes upgrade"

---

### Post by jim_deadlock on 2011-11-16
That looks like just the ticket, thanks!

---

