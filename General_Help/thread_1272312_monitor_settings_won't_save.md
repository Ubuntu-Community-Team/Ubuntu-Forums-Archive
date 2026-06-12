---
title: "monitor settings won't save"
date: 2009-09-22
forum: General Help
---

### Post by chaotzu on 2009-09-22
I'm using a dual screen and I have to configure my monitors when I start up linux. Because I can't save it I have to keep configuring it. I also need to save it to configure seperate x screens, because my screens are different dimensions. If I try to save the configuration i just get an error saying it couldn't save. Any help is appreciated, thanks.

---

### Post by wojox on 2009-09-22
If this nvidia open a terminal and type:

```
gksudo nvidia-settings
```

And you can save it.

---

### Post by scouser73 on 2009-09-22
You need to open the nVidia X Server Settings as root, please copy and paste this command into terminal: **gksudo nvidia-settings**

Then go to **X Server Display Configuration** then set up your monitors to your liking, once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

