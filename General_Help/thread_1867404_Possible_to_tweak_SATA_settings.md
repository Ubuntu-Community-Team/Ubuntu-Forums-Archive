---
title: "Possible to tweak SATA settings?"
date: 2011-10-22
forum: General Help
---

### Post by listerdl on 2011-10-22
I keep getting this error in the log viewer when using an SSD drive and ubuntu:

```

limiting SATA link speed to 1.5 Gbps
ata4: hard resetting link
```

I have updated the BIOS and believe me tried eveything - but - finally I have (I think) discovered why the drive is being limited to SATA 1 and not allowed to go to SATA 2 - this is due to the machine being a toughbook and not allowing you to go to SATA 2 b/c the system doesn't have a fan and the increased heat would cause problems....

[B]So - my question!
[/B]
Rather than have the machine try and reset the SATA speed - is there a way to stop or rather "fix" the SATA speed, i.e. tell ubuntu and the kernel to not bother trying to get faster speeds because it simply wont win this one?

Thanks!!!!

---

