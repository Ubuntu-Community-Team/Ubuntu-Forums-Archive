---
title: "Help with boot kernel boot options"
date: 2006-02-10
forum: General Help
---

### Post by cetol on 2006-02-10
I was browsing the /var/log/kernel.log and found this:

```
Feb 10 09:14:52 localhost kernel: [4294672.231000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
```

I have an NFORCE2 chipset which I know supports 133MHZ bus. How can I pass this on to the kernel at boot?

Or is it even necessary?

---

### Post by dcstar on 2006-02-10
[QUOTE=cetol]I was browsing the /var/log/kernel.log and found this:

```
Feb 10 09:14:52 localhost kernel: [4294672.231000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
```

I have an NFORCE2 chipset which I know supports 133MHZ bus. How can I pass this on to the kernel at boot?

Or is it even necessary?[/QUOTE]
No:

[http://www.linuxquestions.org/questions/showthread.php?threadid=57884](http://www.linuxquestions.org/questions/showthread.php?threadid=57884)

---

