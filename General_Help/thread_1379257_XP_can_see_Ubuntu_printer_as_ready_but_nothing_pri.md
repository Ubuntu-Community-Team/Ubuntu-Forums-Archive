---
title: "XP can see Ubuntu printer as ready but nothing prints"
date: 2010-01-12
forum: General Help
---

### Post by subsoniks on 2010-01-12
I have my Epson C46 working on my Ubuntu 9.10 machine, my XP machines are showing the printer as ready and will send a test page to the Ubuntu printer but it doesn't arrive at Ubuntu - doesn't show in the print job list on Ubuntu but does in XP??
File sharing is now working in both directions.

---

### Post by prshah on 2010-01-12
> **subsoniks said:**
> XP machines are showing the printer as ready and will send a test page to the Ubuntu printer but it doesn't arrive at Ubuntu - doesn't show in the print job list on Ubuntu but does in XP??

Are you running a firewall (such as ufw) on your Ubuntu machine? Check with these terminal (Applications-Accessories-Terminal) commands```
sudo ufw status
``` If it shows as running, try temporarily disabling it with ```
sudo ufw disable
``` and then give your printjob and see if the printer receives it. 

In either case, after a reasonable amount of time (about 3 mins max), please re-enable your Ubuntu firewall with```
sudo ufw enable
```

If it works with the firewall off, you need to allow a particular port through your firewall. If you post your results, we can investigate which port is required (maybe 515 or 9100/1/2/3...?)

---

### Post by subsoniks on 2010-01-12
Thanks for your reply.

Firewalls in both XP and Ubuntu are disabled, I had already checked that before posting as I was previously having problems with file sharing.

---

### Post by subsoniks on 2010-01-14
Bump

---

