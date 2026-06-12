---
title: "Computer name conflict"
date: 2012-02-08
forum: General Help
---

### Post by Custom Cowboy on 2012-02-08
I need to find out how to access and change the name of the computer as seen on a home network. I have a conflict caused by hard drive swapping and would like to avoid the task of reinstalling and choosing a different name during the install. I am running 10.1 Thank you

---

### Post by sikander3786 on 2012-02-08
Get to a Terminal and run:

```
gksudo gedit /etc/hostname
```

In the file that opens up, you'll see you current computer name. Change it to whatever you want and save and close this file.

Again from Terminal:

```
gksudo gedit /etc/hosts
```

In the second line probably, you'll see your computer name. Change it to the same one you used in the first file. Save and close this file and reboot.

Not to say that please be careful and don't change any other settings in any of these files.

---

### Post by Custom Cowboy on 2012-02-08
Thanks for that, you have saved me a reinstall and taught me some more about the system

---

