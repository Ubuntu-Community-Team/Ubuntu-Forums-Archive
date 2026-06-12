---
title: "How can I fix my ethernet connection?"
date: 2012-05-17
forum: General Help
---

### Post by r0fls on 2012-05-17
Hello,

I have ubuntu 12.04 LTS and Windows 7 dual booting on separate hard-drives. When I boot linux, it doesn't connect to the internet even though it shows it's status to the ethernet cable as if it were. I made a .sh file containing:

   #!/bin/bash
   ifconfig eth0 up
   dhclient

and added it to /etc/rc.local, which works to get me connected and stay connected if I run it myself with sudo, but not through adding it to this rc.local file. Adding it to the rc.local file was supposed to run it as root, based on previous research.

Does anyone know what I can do to keep troubleshooting this or solve my problem? I've looked into installing new drivers, but apparently that should be done automatically. I also get a message saying "Could not get the system bus. make sure the message bus daemon is running!" when I shut down using "shutdown 0," but not when I shut down normally with the GUI, though it still freezes instead of shutting down.

Supposedly the problem with the dual-boot can be caused by Windows not releasing the ip address, which I have created a .bat file to do when Windows shuts down, so that shouldn't be the issue.

Thanks in advance!
r0fls

---

