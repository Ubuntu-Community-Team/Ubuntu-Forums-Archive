---
title: "No access to home - all profile settings disappeared after password change"
date: 2011-08-09
forum: General Help
---

### Post by mcemsi on 2011-08-09
Hi guys,

after a period of 3 months I had to change my ubuntu account password on my workstation.

Immediately after the change it seemed to work fine, but when I rebooted all the icons on the desktop, my personal data and themes account settings were gone.

I got an error that there was a problem with a file in my home directory. (I think .ICAccount or s.th like that) I don't remember the correct name, because I bypassed it using chmod 755 on my home directory.

No I dont get any error message but the files in my home folder and all settings are still gone.

There is a README.txt in my home folder:

> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-privateI can mount it by using the command but that doesn't fix the settings problem and the data that was previously stored on my Desktop doesn't apper. I also dont want to have an encrypted home directory. I didn't use that before. I'm using the whole disk LVM encryption that I applied using the alternate installation cd.

I hope there is anyone that can help me.

Thanks a lot in advance.

---

### Post by dino99 on 2011-08-09
[http://ubuntuforums.org/showthread.php?t=923032](http://ubuntuforums.org/showthread.php?t=923032)

[http://askubuntu.com/questions/36049/clone-user-profile](http://askubuntu.com/questions/36049/clone-user-profile)

---

### Post by mcemsi on 2011-08-09
Hey,
thanks for your reply, but if i run the adduser command in the first link, it tells me that the user already exists

---

