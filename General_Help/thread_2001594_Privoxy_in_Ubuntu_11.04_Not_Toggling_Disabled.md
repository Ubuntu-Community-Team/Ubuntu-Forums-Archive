---
title: "Privoxy in Ubuntu 11.04 Not Toggling Disabled"
date: 2012-06-11
forum: General Help
---

### Post by nicksmith on 2012-06-11
Has anyone ever tried using Privoxy in it's disabled mode so it acts like a dumb proxy? I've tried setting to to toggled off in the config file, and whilst the web configuration tools show it as being disabled it's still applying filtering.

Is it a case of the package has been built with the toggle disabled so it's always running in enabled mode no matter what, or something else?

Thanks!

---

### Post by SleepWalkerX on 2012-06-11
Are you using a custom filter?  

How are you testing to see if the filtering is applied?

---

### Post by nicksmith on 2012-06-11
No custom filters, everything 'stock'. Also just done a clean install just to be on the safe side.

Testing it by opening up either Yahoo! Mail, Reddit or MapQuest and seeing if the site loads correctly, then testing it by loading a page with advertising to see if the ad's are loading. No to both questions.

---

### Post by SleepWalkerX on 2012-06-11
I think it disables correctly for me.  Go to aol.com.  Do you see the ad on the right?

---

### Post by nicksmith on 2012-06-11
I don't, (redirects to British site, but same logic). That's with having remove it (apt-get purge) and reinstalled from scratch from apt-get install.

---

