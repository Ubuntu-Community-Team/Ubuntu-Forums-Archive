---
title: "where are packages after apt-get install"
date: 2006-03-19
forum: General Help
---

### Post by mitjab on 2006-03-19
where are packages which were downloaded after apt-get install. I want to delete it becouse i only have 7 GB space left.

---

### Post by Ramses de Norre on 2006-03-19
sudo apt-get clean
They're stored in /var/cache/apt/archives.

---

### Post by engla on 2006-03-19
"sudo apt-get clean" cleans the cache of downloaded packages... that should free up quite a bit for you. It's best to use the tools to clean this thing rather than going there and cleaning it youself (somewhere deep in /var/cache), so nothing unexpected happens.

---

