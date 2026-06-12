---
title: "rkhunter output (possible rootkit)"
date: 2010-11-09
forum: General Help
---

### Post by gandaran on 2010-11-09
> Warning: Network TCP port 60922 is being used by /usr/lib/chromium-browser/chromium-browser. Possible rootkit: zaRwT.KiT
         Use the 'lsof -i' or 'netstat -an' command to check this.
got this checking rkhunter logs but running rkhunter shows nothing suspicious, should I be worried?

---

### Post by Rubi1200 on 2010-11-09
Run the following commands:

```
sudo lsof -i -n -P
```

```
sudo netstat -tulnp
```

Post the output here if you are still unsure.

You should know that tools like rkhunter produce a lot of false positives.

Hope this helps.

---

