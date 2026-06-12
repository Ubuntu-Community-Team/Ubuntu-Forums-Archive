---
title: "Automatic module insert in power up"
date: 2011-09-18
forum: General Help
---

### Post by Yacobh1 on 2011-09-18
Hello everyone,
 
I ask for help to insert/install module automatically in power up.
 
I use Ubuntu 11.04.
 
I try to insert a module automatically in power up.
 
I added the name of my module (hello) to the file /etc/modules.
 
I copied the the file hello.ko to the following directories:
 
- /lib/modules/2.6.38-8-generic/kernel
- /lib/modules/2.6.38-8-generic/kernel/drivers
- /lib/modules/2.6.38-8-generic/kernel/drivers/hello
 
The hello module prints (printk) message to kern.log and responds to open/read/write/ioctl and close functions.
 
I don't see the init log messages in the kern.log file.
 
While I use "insmod hello.ko" command, the command succeeds and I see the log messages.
 
Can anyone help me why the automatically insertion of the module does not succeed?
 
Thank you.
 
Yacob.

---

