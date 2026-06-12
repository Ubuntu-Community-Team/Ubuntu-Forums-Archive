---
title: "Operating systems all missing"
date: 2011-05-01
forum: General Help
---

### Post by THR33 on 2011-05-01
Just upgraded to  11.04. When I restarted it started running memtest. Finished memtest but all of my operating systems are missing. I cant get into ubuntu or windows. They have vanished and the only thing I can do is just endlessly run memtest.

---

### Post by THR33 on 2011-05-01
Help?

---

### Post by idoitprone on 2011-05-01
[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html) Try to follow this guide and boot to ubuntu. When you get into ubuntu try ```
sudo update-grub
```

I want you to try this methods, since it is the fastest method.

btw: bump after 24 hours ok?

or else [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and post the result

---

### Post by THR33 on 2011-05-01
I don't have a grub menu.

---

### Post by Quackers on 2011-05-01
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

