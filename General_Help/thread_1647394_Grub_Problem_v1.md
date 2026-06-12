---
title: "Grub Problem v1"
date: 2010-12-17
forum: General Help
---

### Post by Pegasus_Online on 2010-12-17
Hey guys, I have a problem to solve ...
I have the Grub v1 when I switched to Ubuntu 10.10 retains all settings LTS version 10.04 kept the Grub configuration, Samba Server, etc.

Anyone knows why does not the countdown serves to initiate the default OS??

Anyone know how to activate it or update the Gurb without failures or problems?

Thanks Salu2 Pegasus.

---

### Post by sikander3786 on 2010-12-18
Instead of offering a solution right away, I would suggest to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would exactly tell us about your Grub, settings and boot and thus we'll be able to advise accordingly.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

10.04 uses Grub2 and even 9.10 also so we would like to see which version of Grub is there.

Also, post the outupt of this command.

```
cat /etc/default/grub
```

Thanks.

---

