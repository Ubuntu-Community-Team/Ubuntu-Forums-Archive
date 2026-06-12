---
title: "Chown Problems"
date: 2009-10-03
forum: General Help
---

### Post by justifiedjfreak on 2009-10-03
I have a Semi permanent external HD that I have connected to system. I have been using ubuntu for about a year on and off so I know about chown and how it works. My problem is the drive is owned by root and I sudo into root and do a "chown -R username /media/drivename" obviously I substitute username and drivename with my user and drivename... anyways terminal gives me no errors so I thought that it was good as usuall no new is good news.... right? but then I check the ownership and its still root

---

### Post by arrange on 2009-10-03
What's the filesystem on the drive? How do you mount it?

OR - with the drive attached, post the output of ```
mount
```

---

