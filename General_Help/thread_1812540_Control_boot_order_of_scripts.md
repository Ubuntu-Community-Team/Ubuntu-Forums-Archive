---
title: "Control boot order of scripts"
date: 2011-07-26
forum: General Help
---

### Post by HarriU11-04 on 2011-07-26
hello

i have dansguardian and squid installed in 11.04 and i've noticed that on boot up i do not have Internet access although I have a connection. Ie, pinging a website from the command line works, but loading a webpage from a browser doesn't. i've also noticed that if i restart squid followed by a restart of dansguardian, all problems are resolved.

i would like to change the order of these two scripts, and/or delay the running of them, so that i do not have to manually put up the webfilter every time. i've looked at rc*.d and the scripts, but i'm still new to linux, i'm afraid.

Please note: ufw is enabled; and iptables configured to re-route direct access to the internet or proxy back through Dansguardian.

any tips/advice gratefully received

---

### Post by zero2xiii on 2011-07-26
There is a program in the repro's that start programs serialy, can recall the name.

The second option would be to write a simple batch script to do what you must do manualy, and add it as an startup script.

---

### Post by JKyleOKC on 2011-07-26
The file /etc/rc.local is your best friend in situations such as this. It gets executed as the very last step of the boot process, which means that all the other processes have run by the time it starts, and it's a script, which means that you can failor its actions to meet your specific needs.

The default file does nothing at all except "exit 0" so you need to insert the commands you want executed just before that "exit 0" line in the file. And you'll need to use "gksudo gedit" or "sudo vi" to do the editing since the file is writable only by the super user.

I would add three lines. The first would be the command to restart squid, followed by "sleep 1" to give the restart time to complete, and finally the command to restart dansguardian. Since this file executes as "root" rather than as your own user ID, no "sudo" prefix is necessary -- in fact, using one will make the system appear to hang since it will be waiting for a password that does not exist.

Hope this helps!

---

### Post by HarriU11-04 on 2011-07-27
> **JKyleOKC said:**
> The file /etc/rc.local is your best friend in situations such as this. It gets executed as the very last step of the boot process, which means that all the other processes have run by the time it starts, and it's a script, which means that you can failor its actions to meet your specific needs.

The default file does nothing at all except "exit 0" so you need to insert the commands you want executed just before that "exit 0" line in the file. And you'll need to use "gksudo gedit" or "sudo vi" to do the editing since the file is writable only by the super user.

I would add three lines. The first would be the command to restart squid, followed by "sleep 1" to give the restart time to complete, and finally the command to restart dansguardian. Since this file executes as "root" rather than as your own user ID, no "sudo" prefix is necessary -- in fact, using one will make the system appear to hang since it will be waiting for a password that does not exist.

Hope this helps!
Great! I shall give this a go the next time I reboot. Thanks for your help.

---

