---
title: "Flash &amp; General Ubuntu Issues"
date: 2011-10-28
forum: General Help
---

### Post by majam on 2011-10-28
I have recently migrated from Windows 7 to Ubuntu and am running a dual boot setup; the only things stopping me from solely using Ubuntu are the issues I have been having with Flash and a few general issues.

The problem I have with Flash is that it has slow performance. I am running 64bit Ubuntu and any time I watch a video and click pause, it will have a one second delay between clicking and actual pausing. The same happens when pressing play. This isn't such a big deal, but often the video container will just die and vanish. It does not give an error message or crash the browser, it just looks as if it has failed to load (which is very annoying if you have a 20 minute video loaded and waiting to be watched). I have googled around and found others having some slightly similar issues but have never managed to find a fix.

One other question I have is about Ubuntu performance. I have always thought Linux would perform faster than Windows, but often it is slow and laggy - an example of this would be quickly opening several links in a new tabs on Firefox, it seems to churn along and not handle it very well at all. Again, this example isn't such a big deal but I have found this to be the case across a [narrow] range of activities.

**NB:** I should probably state that I did not install Flash manually - I installed a package that contained a range of essentials like Flash, JRE etc. although I cannot remember the name now. I have installed Flash normally on a 64bit Linux box before though and have had the exact same problem.

Here are my specs:

[B]OS:
[/B]64 bit Ubuntu 10.10

[B]Hardware:
[/B]Intel Core 2 Duo @ 2.10 GHz
4GB DDR2 RAM
80GB HDD (Partitioned from a 250GB HDD; 67GB free remaining)
ATI Radeon HD 4300 (Mobility)

Many Thanks

---

### Post by Bobhuber on 2011-10-28
> **majam said:**
> I have recently migrated from Windows 7 to Ubuntu and am running a dual boot setup; the only things stopping me from solely using Ubuntu are the issues I have been having with Flash and a few general issues.

The problem I have with Flash is that it has slow performance. I am running 64bit Ubuntu and any time I watch a video and click pause, it will have a one second delay between clicking and actual pausing. The same happens when pressing play. This isn't such a big deal, but often the video container will just die and vanish. It does not give an error message or crash the browser, it just looks as if it has failed to load (which is very annoying if you have a 20 minute video loaded and waiting to be watched). I have googled around and found others having some slightly similar issues but have never managed to find a fix.

One other question I have is about Ubuntu performance. I have always thought Linux would perform faster than Windows, but often it is slow and laggy - an example of this would be quickly opening several links in a new tabs on Firefox, it seems to churn along and not handle it very well at all. Again, this example isn't such a big deal but I have found this to be the case across a [narrow] range of activities.

**NB:** I should probably state that I did not install Flash manually - I installed a package that contained a range of essentials like Flash, JRE etc. although I cannot remember the name now. I have installed Flash normally on a 64bit Linux box before though and have had the exact same problem.

Here are my specs:

[B]OS:
[/B]64 bit Ubuntu 10.10

[B]Hardware:
[/B]Intel Core 2 Duo @ 2.10 GHz
4GB DDR2 RAM
80GB HDD (Partitioned from a 250GB HDD; 67GB free remaining)
ATI Radeon HD 4300 (Mobility)

Many Thanks

Follow these directions > FOR JAVA > [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
For flash > Firefox Only > Flash Aid Addon > OR > Download  from the Adobe site and install

  /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by majam on 2011-10-28
> **Bobhuber said:**
> Follow these directions > FOR JAVA > [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
For flash > Firefox Only > Flash Aid Addon > OR > Download  from the Adobe site and install

  /usr/lib/mozilla/plugins/libflashplayer.so

Hi, thanks for the advice but I'm afraid it didn't work.

I used Flash Aid, which seemed extremely promising, and I'm still getting the same problems even after rebooting. Still the pause / play lag, general slow performance and flash just disappearing on me.

I am thinking of formatting my partition and putting a 32bit Ubuntu on (I am wanting to upgrade to the latest version anyway and it shouldn't be too much hassle). Do you think this would sort the issue? That the problem is Flash not being ported well for 64bit boxes?

---

