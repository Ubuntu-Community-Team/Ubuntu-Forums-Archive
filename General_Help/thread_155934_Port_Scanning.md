---
title: "Port Scanning"
date: 2006-04-06
forum: General Help
---

### Post by megahertza on 2006-04-06
I have used the port scanner in network tools, but it is taking too long. I only need to scan between 6881 to 6889. Is there a port scanner for ubuntu where i can limit the scan can i doit through the terminal.

---

### Post by bjweeks on 2006-04-06
Yes, nmap is the king of port scaners and can do what you need.

```
sudo apt-get install nmap
```

---

