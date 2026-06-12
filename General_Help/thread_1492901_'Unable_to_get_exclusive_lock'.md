---
title: "'Unable to get exclusive lock'"
date: 2010-05-25
forum: General Help
---

### Post by John Harris on 2010-05-25
Hi, I am a new user and i have consistently had one problem since i started using ubuntu a couple of days ago, when i try to install or update anything i get the error message 'unable to get exclusive lock'. It says that this probobally means that another software management program is running however using system monitor none are apparent. I am currently trying to use the update manager however i was having the same problem while installing flash player yesterday... does anyone have any suggestions as to how i can resolve this issue? thanks alot, John.

---

### Post by philinux on 2010-05-25
Just to be sure do a reboot.

Then open a terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back what it says.

---

### Post by John Harris on 2010-05-25
thanks for helping, i restarted the computer and typed what you said into the terminal and it came up with the message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I ran sudo dpkg --configure -a

and it came back with the message:
Errors were encountered while processing:
 ttf-mscorefonts-installer

this is consistent with updates in the past, ive even tried manually finding and removing ttf-mscorefonts-installer but it wont let me, this is the file it always stops on.

---

### Post by philinux on 2010-05-25
See post #21.

[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217)

---

### Post by John Harris on 2010-05-25
Thanks Phil, i have made the changes in post number 21 but how can i save changes (i opened it in notepad) but when i try and save, inevitably it says 'access denied'. Where did i go wrong?

---

### Post by philinux on 2010-05-25
Ah yes you need to do it this way.

gksudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

---

### Post by John Harris on 2010-05-25
thanks Phil, you are a legend!

---

