---
title: "Menu tool bar missing in wammu"
date: 2010-10-27
forum: General Help
---

### Post by Vishnu V on 2010-10-27
Hi
 I installed wammu in Ubuntu 10.10 the menu toolbar is missing.
When I tried to open wammu using command the output is
```

vishnu@vishnu-laptop:~/Desktop$ wammu
/usr/lib/pymodules/python2.6/Wammu/MailWriter.py:33: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Debug log created in temporary file </tmp/wammuNPjsS7.log>. In case of crash please include it in bugreport!
Looks like normal program termination, deleting log file.


```
then I changed md5 to hashlib in MailWriter.py then the output is
```

vishnu@vishnu-laptop:~/Desktop$ wammu
Debug log created in temporary file </tmp/wammuYOP1H7.log>. In case of crash please include it in bugreport!
Looks like normal program termination, deleting log file.

```
Screen shot of wammu is attached

Please help
Thanks
Vishnu V

---

### Post by claudio70b on 2010-10-29
I have the same problem using Ubuntu 10.10 and the latest Wammu.

I reported it at [email]gammu-users@lists.sourceforge.net[/email] right now and hope to get response there. :-)

Unfortunately Ubuntu forums do not let unregistered users view attachments. :-P So here is a public screenshot: [http://img241.imageshack.us/img241/9836/screenshotwammu.png](http://img241.imageshack.us/img241/9836/screenshotwammu.png)

---

### Post by Brownout on 2010-11-02
I opened a bug in Launchpad: [LP #669789]("https://bugs.launchpad.net/ubuntu/+source/wammu/+bug/669789").

[QA]("http://en.wikipedia.org/wiki/Quality_assurance") at its best :rolleyes:

---

### Post by Vishnu V on 2010-12-03
Hi 
 Problem solved by removing "appmenu-gtk". Got from [LP #669789]("https://bugs.launchpad.net/ubuntu/+source/wammu/+bug/669789").


Special thanks to Leonardo Montecchi ,Brownout and claudio70b

Thanks you all

---

