---
title: "Disable USB storage device"
date: 2011-02-21
forum: General Help
---

### Post by phanie on 2011-02-21
is there a way or terminal command to disable access to a USB storage device upon insertion given that it is not permitted?

---

### Post by An Sanct on 2011-02-21
Try to use modprobe or even better, the grub option as (both) [described here]("http://www.cyberciti.biz/faq/linux-disable-modprobe-loading-of-usb-storage-driver/").

---

### Post by phanie on 2011-02-21
thnks dude..another thing is, how do you do sudo in a bash.
> "mv /root/usb-storage.ko /lib/modules/2.6.31-14-generic/kernel/drivers/usb/storage/"
as you can see, this code needs to be incorporated in a bash script and it cannot be run because of permission issues.

---

### Post by Spyderkid on 2011-02-21
just simply put sudo or sudo su before the command its not different

but in that case you'll need to be root so put sudo su in so it looks like this....
```

#!/bin/bash
sudo su
mv /root/usb-storage.ko /lib/modules/2.6.31-14-generic/kernel/drivers/usb/storage/

```

---

### Post by Spyderkid on 2011-02-21
also you might want to add an echo in to say its done.

so add in 

&& echo "file moved successfully"

so it looks like....

```

#!/bin/bash
sudo su
mv /root/usb-storage.ko /lib/modules/2.6.31-14-generic/kernel/drivers/usb/storage/
&& echo "file moved successfully"

```

---

### Post by phanie on 2011-02-21
Thank you for the help spyderkid. Im going to test it right away. I'll keep you posted. :P

---

