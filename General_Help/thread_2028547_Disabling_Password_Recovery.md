---
title: "Disabling Password Recovery"
date: 2012-07-18
forum: General Help
---

### Post by stookin on 2012-07-18
Hi  I lost my password. There's a way to recover it right? Good.  How do I disable that option? I don't want anyone to get into my computer. Is that possible? Also, I checked "encrypt Home folder" on installation. Does this mean everything in my Home folder is encrypted? And how secure is it? AES-256?  I hope somebody knows these questions and is willing to help :)

---

### Post by Megaptera on 2012-07-18
For the first question disable p/w recovery - never tried it but this suggested - 

To disable the recovery partition do the following:

The instructions below are only for Grub2 (not the legacy grub) which means we are talking about Ubuntu/Kubuntu 9.04 and later versions.

To disable the recovery mode in Grub, open the following file in an editor as root: /etc/default/grub

Then, uncomment the line with
GRUB_DISABLE_LINUX_RECOVERY=&#8221;true&#8221;

Save the file and let the Grub know about this change by running the following command:
sudo update-grub

Sources: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword), [http://tipstrickshowtos.blogspot.ca/2010/04/how-to-disable-recovery-mode-or-root.html](http://tipstrickshowtos.blogspot.ca/2010/04/how-to-disable-recovery-mode-or-root.html)

Here: [http://herouxapps.com/wordpress/archives/12896](http://herouxapps.com/wordpress/archives/12896)

---

### Post by stookin on 2012-07-18
Thank you so much !

---

### Post by Megaptera on 2012-07-18
You're welcome!

---

### Post by Cheesemill on 2012-07-18
If anyone has physical access to your machine then it's easy for them to get root access, unless you use encryption.

Because you have encrypted your /home folder it makes it difficult for anyone to retrieve your data.

---

### Post by stepking2 on 2012-07-18
To say it simple, AES 256biit means that there are 2^256 possible keys ;-)

---

