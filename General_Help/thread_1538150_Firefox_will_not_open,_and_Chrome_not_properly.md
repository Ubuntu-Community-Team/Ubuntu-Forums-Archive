---
title: "Firefox will not open, and Chrome not properly"
date: 2010-07-24
forum: General Help
---

### Post by Valir on 2010-07-24
Hi, 

I recently restored backuped files onto my Home folder. Since then I haven't been able to open Firefox. Chrome opens but with the error message, that the profile could not be opened properly. 

I have tried bacupin and deleting the .mozilla folder, but Firefox does not create a new one. There are no zombie firefox instances in SysMon. 

What could be the problem?

Would be thankful if anyone knows..

best 

V.

---

### Post by jbrown96 on 2010-07-24
Open firefox from the command line with either ```
firefox -p
``` or ```
firefox -P
``` that will bring up the profile tool and you can force it to create a new one from there.

---

### Post by Valir on 2010-07-26
That didn't work. 

I had to purge everything, erase all firefox folders and build it from scratch. 

[https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds)

That worked.

---

