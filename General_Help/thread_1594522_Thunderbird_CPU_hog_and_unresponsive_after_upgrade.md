---
title: "Thunderbird CPU hog and unresponsive after upgrade"
date: 2010-10-12
forum: General Help
---

### Post by Lightning Jim on 2010-10-12
Ever since I upgraded to 10.10 (via update, not from scratch), Thunderbird suddenly ramps up CPU usage within the 10 seconds of being started. No add-ons are enabled. Anyone have this problem or can help me troubleshoot?

---

### Post by Sigma1 on 2010-10-16
Hi,
Same problem here, after a web upgrade to 10.10. I'd be interested to hear whether you've found a solution! I've tried a) removing extensions, b) removing and reinstalling tbird from scratch.
Thanks in advance.

---

### Post by Sigma1 on 2010-10-17
Last update: downloading tbird 3.1.4 for linux from the mozilla tbird site rather than from the ubuntu depositories seems to have solved the cpu issue.

Basically you need to: remove tbird via synaptics (don't purge everything, if you want to find your mail afterwards!); download the latest tbird from the mozilla site, untar it and place it in /usr/bin (which is where it expects to be), i.e. sudo mv thunderbird/ /usr/bin/, from a terminal.

---

