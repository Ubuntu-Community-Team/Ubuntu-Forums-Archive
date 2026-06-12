---
title: "*** System restart required *** always shows even after a restart"
date: 2010-06-09
forum: General Help
---

### Post by mrotsliah on 2010-06-09
Here is what shows up when I login:

Linux server1 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Wed Jun  9 13:44:41 EDT 2010

  System load: 0.0                       Memory usage: 21%   Processes:       121
  Usage of /:  1.1% of 140.41GB   Swap usage:   0%    Users logged in: 2

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

*** System restart required ***
Last login: Wed Jun  9 13:27:53 2010 from xxx.xxx.xx.xxx


We like the system information about the system load and the memory usage, etc, but "*** System restart required ***" always shows up, even after we restart the server.  Looking at /etc/motd, it has everything that I displayed above.  Notice that the time is given in the motd.  Every time a user logs on the the server, the motd is updated and shows the current system information -- and "*** System restart required ***".  

Why does "*** System restart required ***" not go away after a restart?  Is there a way to keep the system information but get rid of just the "*** System restart required ***"?  

Thanks.

---

### Post by dcstar on 2010-06-10
> **mrotsliah said:**
> Here is what shows up when I login:
........
*** System restart required ***
Last login: Wed Jun  9 13:27:53 2010 from xxx.xxx.xx.xxx
.........
Why does "*** System restart required ***" not go away after a restart?  Is there a way to keep the system information but get rid of just the "*** System restart required ***"?  

Thanks.
This is the script that does this:

/usr/lib/update-notifier/update-motd-reboot-required

All it does is echo the **/var/run/reboot-required** file some other process has put there - check the date stamp of the file.

---

### Post by dcstar on 2010-06-10
> **mrotsliah said:**
> Here is what shows up when I login:

Linux server1 **2.6.32-21**-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
.........
Thanks.

Doh!, I just noticed that and I am running the latest 2.6.32 kernel.

Are you sure that you now don't have a later kernel installed but are not actually booting it?

---

### Post by mrotsliah on 2010-06-10
Let's see;  /usr/lib/update-notifier/update-motd-reboot-required was last updated June 4.  I'll try rebooting again.  

Where would I look to see if there is a more recent kernel on the machine?  

Thanks.

---

### Post by dcstar on 2010-06-12
> **mrotsliah said:**
> Let's see;  /usr/lib/update-notifier/update-motd-reboot-required was last updated June 4.  I'll try rebooting again.  

Where would I look to see if there is a more recent kernel on the machine?  

Thanks.

In whatever package manager you are using (aptitude etc).

Also: [http://www.backports.ubuntuforums.org/showthread.php?t=1012637&page=3](http://www.backports.ubuntuforums.org/showthread.php?t=1012637&page=3)

---

### Post by pgoetz on 2011-06-10
> **dcstar said:**
> This is the script that does this:

/usr/lib/update-notifier/update-motd-reboot-required

All it does is echo the **/var/run/reboot-required** file some other process has put there - check the date stamp of the file.

I checked, and there is no reboot-required file in /var/run.  Nevertheless, I still get this message every time I log in, even immediately after running
 sudo apt-get update
 sudo apt-get dist-upgrade
 reboot

56 packages can be updated.
42 updates are security updates.

*** System restart required ***

---

### Post by pgoetz on 2011-06-10
See this bug report:

[https://answers.launchpad.net/ubuntu/+source/update-motd/+question/156743](https://answers.launchpad.net/ubuntu/+source/update-motd/+question/156743)

---

