---
title: "Auto record voice"
date: 2011-05-16
forum: General Help
---

### Post by conradin on 2011-05-16
Hi everyone! 
about 7 years ago I bought a recording device which had the useful feature of recording just voice, then pausing recoding when vox input was out. there was a little bit of lag, but it worked pretty well. Is there any similar function I can use in the Ubuntu repos?

---

### Post by samichx on 2011-11-09
I've been looking forever too and there are tons of people askgin for an app like that.

There is no single application that performs all of these functions automatically with a GUI but there is a script that you can use that'll record intervals of your choosing.

Here: [http://linuxmoc.wordpress.com/2009/12/04/linux-scanner-recorder-rev-3/](http://linuxmoc.wordpress.com/2009/12/04/linux-scanner-recorder-rev-3/)

Combine that with a cron task ('sudo crontab -e' or 'crontab -e') and you can have each hour, day or week output to a file.

Stuck with the second script on that page with hourly recording on days known to be busy and used the first script for weekend monitoring on the HAM bands.

---

