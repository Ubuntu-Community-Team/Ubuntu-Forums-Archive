---
title: "[ASK] KPackageKit"
date: 2010-05-14
forum: General Help
---

### Post by Arrizqi on 2010-05-14
I have a problem with those package kit. When I download some packages with KPackageKit the speed is very very slow.. My maximum download speed in my home is 110 -120 Kbps (With Internet Download Manager in windows). But when i download some packages with kpackagekit the speed is under 15 Kbps.. Please help me to solve this. Thanks for your attention.



(I'm sorry for my bad english). ^_^

---

### Post by Arrizqi on 2010-05-14
Help me please . . .

---

### Post by ankspo71 on 2010-05-14
Hi,
Have you tried to change your software sources? If not, open KPackageKit, then click on "settings", then click on "Edit Software Sources". Enter your password, then click OK. When the Software Sources window opens, click on the button from "Download From". When the dropdown list appears, select "other". When the "Choose a download server" window opens click on "Select Best Server". It will then check all of Kubuntu's mirrors to select the fastest server for you. You will need to reload the sources cache when it is done.

---

### Post by Arrizqi on 2010-05-15
Thanks very much! Thats work!

---

### Post by kio_http on 2010-05-15
> **ankspo71 said:**
> Hi,
Have you tried to change your software sources? If not, open KPackageKit, then click on "settings", then click on "Edit Software Sources". Enter your password, then click OK. When the Software Sources window opens, click on the button from "Download From". When the dropdown list appears, select "other". When the "Choose a download server" window opens click on "Select Best Server". It will then check all of Kubuntu's mirrors to select the fastest server for you. You will need to reload the sources cache when it is done.

From experience, I will tell you that the pingtest it does doesn't always mean its the fastest. Sometime your "Best server" will be slow. If this is the case chose a server manually.

---

