---
title: "Boot into another OS that exists in GRUB"
date: 2011-04-23
forum: General Help
---

### Post by toxicious on 2011-04-23
I am quite a noob on ubuntu and I am dual-booting it with Windows 7 now. Is it possible via the command line in ubuntu to boot into another OS available in GRUB?

For example I want to be able to just run a script to shutdown ubuntu and then boot windows.

Possible?

---

### Post by lithopsian on 2011-04-23
Certainly possible, but I don't think it is something that is available as a direct function in the way you would want.  I would do it by modifying the default OS to Windows before shutdown, then just letting it rip.  5 minutes later and you'll be working for Bill :)

---

### Post by wilee-nilee on 2011-04-23
[http://sidvind.com/wiki/GRUB:_Boot_another_OS_once](http://sidvind.com/wiki/GRUB:_Boot_another_OS_once)

Looks to be grub-legacy orientated but there is a bash script for toggling.

Here is another with grub2.
[http://fitzcarraldoblog.wordpress.com/2011/04/17/reboot-button-which-allows-you-to-specify-which-grub-2-menu-entry-to-boot/](http://fitzcarraldoblog.wordpress.com/2011/04/17/reboot-button-which-allows-you-to-specify-which-grub-2-menu-entry-to-boot/)

Hey let us know if either work and share the script that does, if you want to.:)

---

### Post by toxicious on 2011-04-23
thank you!
I went with the one for Grub2 as I am using grub2.
I didn't try the whole script, I removed the ability to choose which operating system to boot.

This was the result:

```

#!/bin/bash
sudo grub-reboot 2
sudo shutdown -r now
fi

```

Very much stripped out as you can see.
I did these steps:

1. Edit the file /etc/default/grub to have GRUB_DEFAULT=saved and GRUB_SAVEDEFAULT=true (if it is not already like that). (Had to add the second row)

2. Regenerate the file /boot/grub/grub.cfg (this would only be necessary if you changed anything in /etc/default/grub):

sudo grub-mkconfig -o /boot/grub/grub.cfg


3. Ran this command to get see what the numbers were:
sudo cat /boot/grub/grub.cfg | grep menuentry | awk -F\" '{print N++,$(NF-1)}'


4. Number 2 was my Windows 7 install so therefore I set the grub-reboot to 2.


5. Resulting in the script above.


And it worked flawlessly :)
Now I think I will set these values:


**GRUB_HIDDEN_TIMEOUT=5**
**GRUB_HIDDEN_TIMEOUT_QUIET=false**

 for even faster switching :guitar:
As the grub-reboot command only sets the default boot for next boot I can have the more permanent default boot at ubuntu so when I am in windows, I just need to restart to make it go into ubuntu (it's a htpc so it will only reboot when I want to switch OS).


Thank you again :)

---

### Post by wilee-nilee on 2011-04-23
> **toxicious said:**
> thank you!
I went with the one for Grub2 as I am using grub2.
I didn't try the whole script, I removed the ability to choose which operating system to boot.

This was the result:

```

#!/bin/bash
sudo grub-reboot 2
sudo shutdown -r now
fi

```

Very much stripped out as you can see.
I did these steps:

1. Edit the file /etc/default/grub to have GRUB_DEFAULT=saved and GRUB_SAVEDEFAULT=true (if it is not already like that). (Had to add the second row)

2. Regenerate the file /boot/grub/grub.cfg (this would only be necessary if you changed anything in /etc/default/grub):

sudo grub-mkconfig -o /boot/grub/grub.cfg


3. Ran this command to get see what the numbers were:
sudo cat /boot/grub/grub.cfg | grep menuentry | awk -F\" '{print N++,$(NF-1)}'


4. Number 2 was my Windows 7 install so therefore I set the grub-reboot to 2.


5. Resulting in the script above.


And it worked flawlessly :)
Now I think I will set these values:


**GRUB_HIDDEN_TIMEOUT=5**
**GRUB_HIDDEN_TIMEOUT_QUIET=false**

 for even faster switching :guitar:
As the grub-reboot command only sets the default boot for next boot I can have the more permanent default boot at ubuntu so when I am in windows, I just need to restart to make it go into ubuntu (it's a htpc so it will only reboot when I want to switch OS).


Thank you again :)

You did it as I thought I might, thanks for posting the answer.;)

---

