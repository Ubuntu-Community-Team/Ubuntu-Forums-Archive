---
title: "Apt problem"
date: 2010-05-14
forum: General Help
---

### Post by othiena on 2010-05-14
I am currently using a hp compaq tc4200 with lucid and whenever I try to install packages from any ubuntu cd it will only download the first one and not the other ones. I think it has to do with lucid mounting /media/(name of cd) and not to /media/cdrom0 because if i upgrade it works fine. I am just wondering what package defines the default cdrom mount point?

---

### Post by othiena on 2010-05-14
Help please this is very important!

---

### Post by pedro_orange on 2010-05-14
Have you tried explictly mounting the drive under /media/cdrom0?

```
sudo mount /media/cdrom0
```

---

### Post by othiena on 2010-05-14
yes but apt wont find it. all i want is the .deb package that the cdrom mount mounts points  are in.

---

### Post by ba_saish on 2010-05-15
have you enabled the "installable from cd-rom" in synaptic_package_manager->settings-> repositories->update_software tab.

---

