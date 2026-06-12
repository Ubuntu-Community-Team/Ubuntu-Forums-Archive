---
title: "Ubuntu won't shut down."
date: 2010-05-04
forum: General Help
---

### Post by aNetBean on 2010-05-04
Hi everyone, i started some weeks ago with Ubuntu 9.04 when the update to 10.04 was released. As i was pretty new to linux, i decided to download the 64 bit version. Installation went fine and i love it so far.

But now my issue, when i go to the shutdown button and click 'shutdown', the computer starts shutting down and then shows a black screen saying Ubuntu and a progress bar with red dots, and stays there. I have to shutdown, disconnecting the power to the computer. It does not always do that, any help would be appreciatied. If you need systemspecs i will gladly post them if its any help.

Thanks in advance.:D

---

### Post by nothingspecial on 2010-05-04
Press Ctrl Alt F1

It will ask you to login.

Type your username and press enter.

Then type your password (which you will not see) and press enter again.

Type ```
sudo shutdown -h now
```

Do you get any error messages?

---

### Post by dino99 on 2010-05-04
> **aNetBean said:**
> Hi everyone, i started some weeks ago with Ubuntu 9.04 when the update to 10.04 was released. As i was pretty new to linux, i decided to download the 64 bit version. Installation went fine and i love it so far.

But now my issue, when i go to the shutdown button and click 'shutdown', the computer starts shutting down and then shows a black screen saying Ubuntu and a progress bar with red dots, and stays there. I have to shutdown, disconnecting the power to the computer. It does not always do that, any help would be appreciatied. If you need systemspecs i will gladly post them if its any help.

Thanks in advance.:D

some users have found a work around for them: 

sudo gedit /etc/default/grub

modify the line saying: quiet, splash       to   quiet, acpi=force

---

### Post by aNetBean on 2010-05-04
> **dino99 said:**
> some users have found a work around for them: 

sudo gedit /etc/default/grub

modify the line saying: quiet, splash       to   quiet, acpi=force

This did not have any effect. :(

> 

Press Ctrl Alt F1

It will ask you to login.

Type your username and press enter.

Then type your password (which you will not see) and press enter again.

Type      Code:
     sudo shutdown -h now 
Do you get any error messages?     I pressed, but it didn't change  the screen, nothing happens. 

It is strange because a reboot is no problem.:confused:

---

