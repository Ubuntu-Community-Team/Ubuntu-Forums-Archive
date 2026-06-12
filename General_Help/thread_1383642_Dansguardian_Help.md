---
title: "Dansguardian Help"
date: 2010-01-17
forum: General Help
---

### Post by poptop94 on 2010-01-17
I removed dansguardian due to it being too restrictive. I mean why block root. It's my other users I want to control access for. Anyway, since I couldn't download from launchpad I removed it and now I can't get on the internet at all. Please help, pretty noob. Oh I am using Mint.

---

### Post by cariboo on 2010-01-17
How did you remove dansgaurdian? If you just used the remove option without stopping the service, there are still configuration files around, and dansguardian is probably still running. Stop the service, then in a terminal type:

```
sudo apt-get purge dansguardian
```

This will remove the program and all it's configuration files.

BTW, why does root need to get on the internet?

---

