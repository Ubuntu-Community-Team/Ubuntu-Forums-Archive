---
title: "suspend and hibernate no longer work"
date: 2012-08-13
forum: General Help
---

### Post by sbw87 on 2012-08-13
Hi,

After some updates, suspend and hibernate no longer work on my Thinkpad. pm-suspend does, however. So it's XFCE's suspend which seems to be broken. It just says "no backend supported".

Thanks for any help!

---

### Post by Toz on 2012-08-13
What versions of Xubuntu and Xfce are you using? Is this a straight Xubuntu or an Xfce on Ubuntu install?

When did these updates occur? Can you find out which ones they were? Look at the /var/log/apt/history.* log files.

Anything of relevance in your ~/.xsession-errors or /var/log/syslog files when you attempt a suspend?

What does the following command return?
```
ps -ef | grep -i 'console\|upower'
```

---

### Post by sbw87 on 2012-08-19
I was using the most recent versions. The problem seems to have been resolved by a subsequent batch of updates, so it's all fine now.

---

