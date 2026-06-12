---
title: "Problem with booting"
date: 2010-12-30
forum: General Help
---

### Post by daristi on 2010-12-30
I've installed Ubuntu 10.10 in a computer that previously had windows vista. Before the installation I'd two partitions, C (main partition) and D. So I installed Ubuntu (via a bootable usb) in D and up to that point everything worked fine. Now, the problem is that after restarting the machine I don't have any boot option to access Ubuntu and the system goes directly to windows. Any help will appreciated.

---

### Post by theasprint on 2010-12-30
Hi,

Can you access a LiveCD?

If yes, then boot from a LiveCD (with internet connection) and download the Bootinfoscript in my signature below. 

Post the results (results.txt) in this thread.

This would give you an overview of your current system.

---

### Post by Quackers on 2010-12-30
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

