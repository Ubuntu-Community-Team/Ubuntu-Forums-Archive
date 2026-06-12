---
title: "Ubuntu does not shut down sometimes"
date: 2011-09-20
forum: General Help
---

### Post by chamalsl on 2011-09-20
Hi,

I have Ubuntu 10.04 running on a ASUS k52jt-xt1 laptop.
My problem is sometimes Ubuntu does not shutdown.
When I press shutdown , ubuntu task bar dissapears but wallpaper stays and nothing happens.

This happens when I shutdown after a long memory consuming task such as linking a large program.

Otherwise ubuntu shuts down fine.
What should I do to identify the problem.

Thanks,
Chamal.

---

### Post by scarleo on 2011-09-20
Probably start going through your logs (syslog kern.log etc.) to see what is interrupting or holding shutdown. Have you added any custom scripts to run in /etc/rc0.d/ maybe? Did it start after installing a certain program? Or what changed right before this started to happen?

---

### Post by shashi20008 on 2011-09-20
Login into a tty terminal (by pressing Alt+Ctrl+F2 or Alt+Ctrl+F3 etc) and try rebooting your system from there by issuing "sudo reboot" command (without quotes) or reboot your system after turning off splash screen. This will show you the exact steps system is taking during the shutdown process, consequently you will also see the process that's getting shutdown process struck. Knowing the 'guilty' process's name would easily sort out your problem :-)

---

