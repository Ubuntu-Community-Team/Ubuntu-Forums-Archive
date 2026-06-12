---
title: "Desktop lockup with 12.04"
date: 2012-05-19
forum: General Help
---

### Post by geoffwhi on 2012-05-19
Ever since I've upgraded to 12.04 my desktop has started to lockup.  The mouse still responds but all windows are non responsive.  The same hardware has worked fine since v9.  Memory test is ok.  I can see no errors reported in syslog, dsmeg, xorg, or messages.  Video is AMD ATI M52 driver.  Any suggestions on what to do?

---

### Post by 2F4U on 2012-05-19
Is there any pattern behind the lockup, i. e. happens always when particular applications are running? When it locks up, does it ever come back or is it frozen forever, so that you have to reboot?
It might help to further diagnose the problem if you could have a terminal open and always visible running top or htop. This may show whether a particular process is causing this.

---

### Post by geoffwhi on 2012-05-19
It's locked up with both Firefox and kpatience, annoyingly it upset my 1000 game winning streak at freecell :-(  They are pretty well all I ever have running when it happens.  I can't really see a pattern, it can happen every day or so.    I can't get a terminal from the command keys.  I should also add that it's up to date with update manager.  If I managed to get a terminal running, what should I look for?

---

### Post by 2F4U on 2012-05-19
Well, the terminal thing would only be necessary if you are not sure which application causes the problem. Since you are able to narrow it down to two applications, its not necessary. I don't know kpatience, but I know that Firefox extensions and add-ons can cause problems. Do you have any such extensions or add-ons running?

---

### Post by geoffwhi on 2012-05-19
Nothing different that I've had since v9.  Could a firefox addin  lock up the response fron all windows and keys?

---

