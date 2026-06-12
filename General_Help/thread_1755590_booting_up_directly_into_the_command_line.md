---
title: "booting up directly into the command line"
date: 2011-05-11
forum: General Help
---

### Post by zeelog on 2011-05-11
Is it possible to run Ubuntu without any GUI ?
I would like to start up directly into the command line of
the operating system without having to deal with any GUI at all.
This used to be normal in Linux. Can this be done with Ubuntu ?
 And if so, where would I find out how to do it ?
I hope this question doesn't get everyone upset like my last
question. I'm not asking to upset people. I would just like
to know the answer.

---

### Post by nothingspecial on 2011-05-11
I wasn't upset :)

edit /etc/default/grub 

change

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" 

to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Then type

```
sudo update-grub
```

Then restart

---

