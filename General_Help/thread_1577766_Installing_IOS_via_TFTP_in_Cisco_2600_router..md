---
title: "Installing IOS via TFTP in Cisco 2600 router."
date: 2010-09-19
forum: General Help
---

### Post by melrokz on 2010-09-19
Hi. I'm Melvin, doing a hardware and networking course at Aptech, Kerala, India. 
How to install IOS image (file.bin) via TFTP from Ubuntu to a Cisco 2600 router.
Please post the required steps to configure tftpd in Ubuntu. 
And since it is insecure, please post recommendations to secure it.
Which folder will TFTPd use and what binary permissions to assign to this folder?

---

### Post by The Cog on 2010-09-19
If you install package tftpd-hpa from the repositories, I think it serves from folder /var/lib/tftpboot, so put your IOS images in there. You will need root privileges to put files in there. I recommend the command line:
**sudo cp C2600whatever.bin /var/lib/tftpboot**.

---

