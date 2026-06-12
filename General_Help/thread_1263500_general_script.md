---
title: "general script"
date: 2009-09-11
forum: General Help
---

### Post by petebarchetta on 2009-09-11
hello all,

is there a general script i can create or use that will list every program i have currently installed ionto the laptop?
basically i have a newer (but still old) :) laptop and i want to run / create a autoscript that i can use / execute ont he newer machine to load / install all the current apps that are in the older machine if that makes sense.

---

### Post by P4man on 2009-09-11
makes perfect sense :) And its easy:
On the current machine:
```
dpkg --get-selections > selections.txt
```

Then save that text file, and on the new install do:
```

dpkg --set-selections < selections.txt
apt-get update
apt-get upgrade
```

---

