---
title: "Sudden Long Boots"
date: 2009-09-12
forum: General Help
---

### Post by armware on 2009-09-12
Boot times used to be around 45 seconds, as seen in 'original.png', then something happened, turning my boot times to over 3 minutes, as seen in 'first long.png'. I've also attached the latest bootchart, 'current.png'. I'm sure details are in the logs, but going through them nothing stands out to me, not to mention I'm not too sure where to look. So many log files, the only one named 'boot' is empty, even after enabling boot logging.
First thing I noticed with the long boot times is the hard drive indicator is solid for a nice little while (which i'm assuming is shown in the hd usage chart in the bootchart images), long enough for splashy to timeout. I'm having a heck of a time narrowing down the culprit.
I've gone through with bum, disabled unneededs, and shaved off about 15 seconds, but I've got at least another minute and a half possible.

Ideas? Directions?

---

### Post by frt975 on 2009-09-12
Have you tried profiling? If you've prompted with disk checks, let them run.

---

### Post by armware on 2009-09-12
i have profiled, which was the bulk of the 15 seconds i took off, and i always let it do it's auto scans.

looking closely at the bootcharts, i noticed the 'sh' process is what's causing all the hd activity. how can i look deeper into what is involved with this step?

---

### Post by NoaHall on 2009-09-12
It's the shell.

---

### Post by armware on 2009-09-12
the shell would be running what boot scripts, and how to figure out which one is pounding my hd?
i'll do trial and error, that's not a problem, but where are the scripts ran by this process?

---

### Post by NoaHall on 2009-09-12
I suppose you could blacklist some things from starting up. Add things in here - /etc/modprobe.d/blacklist.conf

---

