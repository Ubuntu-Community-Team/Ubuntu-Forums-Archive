---
title: "run-init: /sbin/init: I/O error"
date: 2011-09-15
forum: General Help
---

### Post by reza_bagheri on 2011-09-15
hi,
I am using Ubuntu 11.04
I always hibernate the system
But yesterday I shut down the system
Today's in boot after grub menu I get this error:
run-init: /sbin/init: I/O error
and system freez!
i' usung meny solution,
using live cd and try to mount and chroot([http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/"))
but after this command:
```
sudo chroot /media/xx..xx[/CODE
(xx is root partition)

i get this error again!
[CODE]'/bin/bash' : Input/output error
```

I have meny file in home folder and install many application
and need them,
what can i do?

---

### Post by sanderd17 on 2011-09-15
Can you mount the partition and read files from it?

If, backup the entire /home directory to an external hard drive.

---

### Post by reza_bagheri on 2011-09-16
> **sanderd17 said:**
> Can you mount the partition and read files from it?

If, backup the entire /home directory to an external hard drive.
I'm use ubuntu 11.04 live cd, 
and mount ubuntu partition

and run nautilus 
```
sudo nautilus 
``` 

set privilage for home folder
but the home foldr is empty!:(

---

### Post by sanderd17 on 2011-09-16
It has to be a hard drive fail. I hope it was only a one-time fail.

I can't do a lot, but you could read this article and try it: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

If you have a backup, don't bother reading that article, you will need to reinstall everything. And if you keep getting such errors, you will need to replace the HDD.

---

