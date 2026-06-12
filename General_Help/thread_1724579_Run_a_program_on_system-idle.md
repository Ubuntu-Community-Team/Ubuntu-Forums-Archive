---
title: "Run a program on system-idle?"
date: 2011-04-08
forum: General Help
---

### Post by micha8l on 2011-04-08
Hey,

Torrents client kills my Internet connectivity so bad I can't even use a web-browser whilst it's on -- pages take like five minutes to load -- I often forget to turn on my torrent client. Which led me to wonder if there's a way I can launch a script on system idle?

Kind Regards,
Mike

---

### Post by Dave_L on 2011-04-08
You can lower its priority by running it with "nice":

```
nice /path/to/script
```

That sets the "nice" value to 10, the default.

---

