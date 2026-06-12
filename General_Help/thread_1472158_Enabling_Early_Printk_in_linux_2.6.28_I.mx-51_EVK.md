---
title: "Enabling Early Printk in linux 2.6.28 I.mx-51 EVK"
date: 2010-05-04
forum: General Help
---

### Post by bkankur on 2010-05-04
Dear Friends,
 
I am using ubuntu on I.MX 51 babbage board from Freescale. With my requirement of showing the  boot logo in redboot, I am trying to debug how the linux shows the  bootlogo. 



For that purpose, I kept the debug messages under  drivers/mxc/ipu3/ using "printk" . I can see the log on console which is  ttymxc0. Now the issue is I cannot able to see the debug messages of  IPU initialization on console. The reason might be the prior  initalization of IPU.
 
Is there any way to get early Printk  debug enable or any other solution to get the debug using printk  function?
 
Have a Good Day,
Thank you,
Ankur.

---

