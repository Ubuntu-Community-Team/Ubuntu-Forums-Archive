---
title: "Removing certain packages without losing ubuntu-desktop ?"
date: 2006-03-22
forum: General Help
---

### Post by Reggie on 2006-03-22
Hi,

I'm cleaning up my ubuntu. There are some tools like cdrecord, wvdial, etc. which I don't need. When trying to completely remove the tool with Synaptic, the package manager says I "ubuntu-desktop" will be removed too.
Why is that ? That's a part of my gui if I'm correct ? Is there any way to ONLY remove the tool without anything else ?

---

### Post by Stealth on 2006-03-22
Removing ubuntu-desktop won't delete your gui and stuff. Its a metapackage that will refer to all the main ubuntu apps and stuff for installations. The only thing is when you wanna update to dapper or something, it will einstall those programs along with ubuntu-desktop. But you can safely remove them again, and ubuntu-desktop without worrying about destroying Ubuntu.

---

### Post by Reggie on 2006-03-22
Ok, I hope I can rely on your ubuntu-knowage :) Cause I don't feel like reinstalling ubuntu again :p

---

### Post by Reggie on 2006-03-22
Is there any website where I can see wich ubuntu packages are safe to remove ? I'm kinda new to ubuntu.
I got another linked package Synaptics wants to remove: "ubuntu-minimal"

---

### Post by bonzodog on 2006-03-22
ubuntu-minimal again is a 'meta-package', which is used for install only to refer to packages to install. it won't affect anything.

---

