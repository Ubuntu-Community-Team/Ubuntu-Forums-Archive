---
title: "Save home folder to removable media on logout"
date: 2010-03-13
forum: General Help
---

### Post by olmecnz on 2010-03-13
I maybe trying to reinvent something that already exists. Please let me know whatever is the best way to do this.

What I am attempting to achieve is to sync files from my home drive to a removable drive on logout and back when I login. The rationale is that if I have this system implemented on 2 machines my home folder will 'follow' me from machine to machine via USB thumb drive (/media/usb).

I have created appropriate scripts to perform the necessary file transfers (using rsync) and some basic logging.

To execute on logout I added the script to /etc/gdm/PostSession/Default and tested. It gets executed (by root) but it seems that the removable device has been unmounted prior to the script being run.

Any ideas on how to achieve this type of functionality? Basically roaming profile via USB... Google doesn't offer much hope.... Help much appreciated.

---

