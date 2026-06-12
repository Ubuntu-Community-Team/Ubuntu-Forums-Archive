---
title: "Cron job between every 10 minutes 8am and 2am"
date: 2012-08-07
forum: General Help
---

### Post by fixles on 2012-08-07
Hi,

I'm trying to create a cron job that runs every 10 minutes between 8am and 2am the following day but cant work out how to do it.

I tried 

*/10 8-2 * * * scriptname

which didn't seem to run at all even though it installed without error.

So i tried creating 2 jobs but it didn't start again this morning
*/10 8-0 * * * scriptname
*/10 0-2 * * * scriptname

any idea how I can achieve this?

I'm using ubuntu 12.04 64bit.

Thanks.

---

### Post by jim_deadlock on 2012-08-07
Try this:

*/10 0-2,8-23 * * *

...or:

*/10 0,1,2,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23 * * *

---

### Post by wojox on 2012-08-07
Where is the script located? Are you using the proper path?

---

### Post by jim_deadlock on 2012-08-07
Good point, you should first make sure that cron is able to run the script at all before you start messing with the timings. When you run it via normal user session there are many environment variables available which are not necessarily available during a cron job.

---

### Post by fixles on 2012-08-08
> **jim_deadlock said:**
> Try this:

*/10 0-2,8-23 * * *


Your a legend worked a treat thanks!

---

