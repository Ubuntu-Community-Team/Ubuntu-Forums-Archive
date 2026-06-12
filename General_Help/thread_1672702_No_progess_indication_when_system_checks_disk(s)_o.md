---
title: "No progess indication when system checks disk(s) on start up"
date: 2011-01-21
forum: General Help
---

### Post by mashedbear on 2011-01-21
Ubuntu 10.10 does not appear to have an indication of progress when the system checks HDs on start up. In previous versions - at least back to 8 - I think there was either a progress bar or % reading to give an indication of progress of the scan / check .

Is it possible to switch this back on in 10.10?

Also how do you control the frequency of disk checks on start up?

Cheers

---

### Post by tredegar on 2011-01-21
> Also how do you control the frequency of disk checks on start up?
Please see **man tune2fs **
You'll need to pay attention to the **-c** and **-i** options

---

### Post by mashedbear on 2011-01-23
Thanks - really helpful - the next check interval is 6 months - I guess this is the default and is fine. 

cheers

---

