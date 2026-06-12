---
title: "New installation"
date: 2011-09-09
forum: General Help
---

### Post by hezy00 on 2011-09-09
Hello,
I'm trying to install Ubuntu 11.04 on a second HD but after I choose partition and click the install button, it says that no root or path selected on an error message.How should I select it and continue the installation? Thanks,
Hezy, :).

---

### Post by howefield on 2011-09-09
After selecting the partition, did you click the change button and mount as appropriate ?

---

### Post by 3rdalbum on 2011-09-09
> **hezy00 said:**
> Hello,
I'm trying to install Ubuntu 11.04 on a second HD but after I choose partition and click the install button, it says that no root or path selected on an error message.How should I select it and continue the installation? Thanks,
Hezy, :).

You don't just "click the partition and click Install"; you have to tell it what you want to use that partition as. Click the partition and click Edit, and then change the "Mount point" to /

/ is basically the Ubuntu filesystem.

Once you have at least a / (and preferably a "swap" partition too if you don't have much RAM - this doesn't require a mount point, just needs to be formatted as Linux Swap) you can install.

---

### Post by hezy00 on 2011-09-09
i don't remember that option... I'll try again considering the following  Re as well.

---

### Post by hezy00 on 2011-09-09
Hi again. I managed with the installation only it runs very very slow... What else, when I enter a key in the WEP connection box, the 'connect' button stays Inactive. It's 32 bit. Thanks,
Hezy.

---

