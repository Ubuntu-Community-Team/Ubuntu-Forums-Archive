---
title: "Further Work on my script"
date: 2010-11-29
forum: General Help
---

### Post by Spyderkid on 2010-11-29
Ok, I would like to be able to further develop my script for re-compiling my wireless driver this is what I've got so far...

```
 #!/bin/bash
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
cd driver
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
make clean && make && sudo make install
  
```

I would like to be able to further develop this by adding in a extra thing:
>how to make the computer restart after the script has finished running (so giving the option of y/N.)

Also to run the file I know you can click on the file and click run in terminal, or do you do ./ to run the file in terminal. I can't remember


*Cheers!*

---

### Post by Spyderkid on 2010-11-30
Bump, I would really like to be able to get this done.

---

### Post by nothingspecial on 2010-11-30
For a yes or no answer you can use read
```

echo "reboot?"

read answ
if [ "$answ" = "y" ]
then
        sudo reboot
else
        echo "ok"
fi
```

That will actually reboot if you type y, and not if you type anything else but I`m just trying to get you going, while I cook my kids tea. :D

---

### Post by Spyderkid on 2010-11-30
thanks ill give it a go.

---

