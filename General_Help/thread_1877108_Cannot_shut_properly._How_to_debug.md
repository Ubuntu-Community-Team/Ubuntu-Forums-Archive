---
title: "Cannot shut properly. How to debug?"
date: 2011-11-07
forum: General Help
---

### Post by silentwol on 2011-11-07
I'm running a fresh install **myth**buntu 11.10 (hope this is the right place to ask... sorry if not!).

The problem I'm having is that the computer won't completely shut down.  After leaving the shutdown process for some time and pressing escape to view the status, I see many 'shutting down .... OK' (as expected).  The last entry is 'All processes terminated in 2 seconds' and then the computer just keeps running.

Is there a way to debug this?  Any log files to look at?

I've already extensively googled the problem. The only thing I could find was a suggestion to use 'shutdown -P now', but the exact same problem happens when I try this.

Thanks for your help! :)

---

### Post by Frogs Hair on 2011-11-07
The Link will describe a way to view a shutdown record , but I don't know if errors will be displayed because I have had no problems . when I run the command it simply shows a record of when the computer was shutdown .  

[http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html](http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html)

---

### Post by Elkimo on 2011-12-02
I had a similar problem. Would you happen to have changed the settings of LibreOffice to activate the quickstarter? I don't know if Mythbuntu has LibreOffice.

In my case, disabling the LibreOffice quickstarter somehow solved my shutdown problems.

---

