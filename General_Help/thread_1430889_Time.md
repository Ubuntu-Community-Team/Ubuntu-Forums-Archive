---
title: "Time"
date: 2010-03-15
forum: General Help
---

### Post by Bert_421 on 2010-03-15
I have changed back to 9.04 from 9.10 Because Firefox has done something to there browser 3.5 and up will not work correctly. 
 
Why is my system changing time?
 
I have 9.04in and extra drive with my extra files for windows (two partions) i have windows 7 on the raid drive when i switch back to window 7 from 9.04 time is bump ahead 6+ hours.
 
All the setting in 9.04 is set to my city time is correct in 9.04 but when i switch to windows 7 the system is bumped

---

### Post by dcstar on 2010-03-15
> **Bert_421 said:**
> I have changed back to 9.04 from 9.10 Because Firefox has done something to there browser 3.5 and up will not work correctly. 
 
Why is my system changing time?
 
I have 9.04in and extra drive with my extra files for windows (two partions) i have windows 7 on the raid drive when i switch back to window 7 from 9.04 time is bump ahead 6+ hours.
 
All the setting in 9.04 is set to my city time is correct in 9.04 but when i switch to windows 7 the system is bumped

Ubuntu uses UTC offset by the timezone you selected during install, if this is correct then Windows is not set to use the correct time.
```
sudo tzselect
```
Change the Linux UTC setting here:
```
gksudo gedit /etc/default/rcS
```

---

