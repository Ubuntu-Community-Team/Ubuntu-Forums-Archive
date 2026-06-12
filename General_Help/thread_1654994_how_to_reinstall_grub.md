---
title: "how to reinstall grub?"
date: 2010-12-29
forum: General Help
---

### Post by rockager on 2010-12-29
can someone give me a step by step procedure for reinstalling grub? (i'm a total n00b)

---

### Post by spiky001 on 2010-12-29
Why do you need to reinstal, and what version are you using?

---

### Post by cottfcfan on 2010-12-29
Assuming your using Grub2.
Boot into the live CD.
Open a terminal and mount the partition your installation is on.
for eg if your on sda1
```
sudo mount /dev/sda1 /mnt
```
then:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
You should then get a message saying whether successful or not.
Then Reboot, enter a terminal and type:
```
sudo update-grub
```
Done.

---

### Post by ruben_linux on 2010-12-29
two interesting video:

[http://www.youtube.com/watch?v=WtBBl6HvdpM](http://www.youtube.com/watch?v=WtBBl6HvdpM)

[http://www.youtube.com/watch?v=MDRBffouUto&feature=watch_response](http://www.youtube.com/watch?v=MDRBffouUto&feature=watch_response)

I hope they are useful

---

