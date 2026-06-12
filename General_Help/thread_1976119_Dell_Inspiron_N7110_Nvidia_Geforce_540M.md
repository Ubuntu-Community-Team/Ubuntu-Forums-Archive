---
title: "Dell Inspiron N7110 Nvidia Geforce 540M"
date: 2012-05-08
forum: General Help
---

### Post by Deagle13 on 2012-05-08
Hello Ubuntu fellows!

I am using Ubuntu 12.04. Is there any solution for setting in the title mentioned graphic card?
I've tried many solutions but none of them didn't work :(

Does anyone have any info if developers are already fixing this bug?

Thank you in advance.

Kind regards, Deagle13

---

### Post by 2F4U on 2012-05-08
It is not clear to me from your post what the exact problem is. Are you unable to boot the machine, do you have problems installing proprietary nVidia drivers, or something else.

---

### Post by veroslav on 2012-05-08
He probably is having problems installing nVidia drivers, which normally show up in the Additional Software dialog, but I think this is not the case in Ubuntu 12.04 IF you are having an Optimus laptop (nVidia/intel), because installing nVidia drivers on such a laptop leads to breakage on the restart.

I think what OP needs to do is outlined here:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Btw, I have an exactly the same laptop and I had to disable nVidia card for better power management.

---

### Post by veroslav on 2012-05-08
Also, I think that if the output of the command below shows two entries (one each for nVidia and Intel cards respectively) then it is definitely an Optimus laptop and Bumblebee should be installed:

```
lspci | grep VGA
```

---

### Post by Deagle13 on 2012-05-09
Hello!

I am so sorry if my post wasn't clear enough. I can't make Nvidia drivers to work... I can boot
the system in 640x480 resolution. Than I have to reconfigure the X to get back to the integrated graphic.

Kind regards, Janez

---

### Post by smurphy on 2012-05-09
Just make sure you install the restricted NVIdia drivers.
Works on my mac Mini here - only have the NV320 though ...

---

