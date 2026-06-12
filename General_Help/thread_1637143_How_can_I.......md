---
title: "How can I......"
date: 2010-12-04
forum: General Help
---

### Post by Spyderkid on 2010-12-04
how can I make my script automaticly run after restarting after updates, is it possible?

this is what I've got so far...

```

#!/bin/bash
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
cd driver
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
make clean && make 
sudo make install && sudo modprobe 8712u && echo "8712u" | sudo tee -a /etc/modules &&
echo "reboot?"

read answ
if [ "$answ" = "y" ]
then
        sudo reboot
else
        echo "ok"
fi

```


Also what does else do and fi can I find out by putting man before it in a terminal?

---

### Post by Spyderkid on 2010-12-05
bump even a no its not would be nice

---

