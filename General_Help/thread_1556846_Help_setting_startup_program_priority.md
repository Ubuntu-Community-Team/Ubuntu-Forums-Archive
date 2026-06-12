---
title: "Help setting startup program priority"
date: 2010-08-20
forum: General Help
---

### Post by ngrieb on 2010-08-20
I am attempting to change the boot priority of a startup script that I wrote, but when I change the priority level in the gnome-system-monitor but upon reboot the permissions reset themselves. Why is this happening? I do get a warning from the gnome-system-monitor when attempting to run sudo gnome-system-monitor that says SELinux was found but is disabled. From what I gather SELinux is a security measure that prevents high level changes. Is it resetting the boot priorities? If so how do I fix this? Thanks in advance.

---

### Post by ngrieb on 2010-08-20
Never mind I got it to work via the "nice" command. I just think that the priorities set in the system monitor should stick as well.

---

