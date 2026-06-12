---
title: "parse mac address from arp -a"
date: 2011-01-24
forum: General Help
---

### Post by gecko91 on 2011-01-24
Hi,
I'm using arp -a to get the mac address of the router I am connected to. This is the first line of the output:
```
? (153.106.80.1) at 0:50:3e:97:dc:a on en1 ifscope [ethernet]
```I want to grab the mac address from this. I know that I probably need to use sed with a regular expression like [0-9A-F]\+: but I am not sure how to do this.

Thanks,
geck0

---

### Post by Cheesehead on 2011-01-24
```
arp -a | cut -d' ' -f4                         # Get the MAC address from each line
arp -a | grep $line_criteria | cut -d' ' -f4   # Get the MAC address from a specific line

```

---

