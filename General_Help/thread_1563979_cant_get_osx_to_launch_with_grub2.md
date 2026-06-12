---
title: "cant get osx to launch with grub2"
date: 2010-08-29
forum: General Help
---

### Post by zms on 2010-08-29
I have an acer aspire one. I had iPC osx86 10.5.6 installed on it. then I installed ubuntu 10.04.1 and now i cant get OSX to start up. OSx shows up in grub but when i select it i just get a blank screen. I have been exploring the world of google for a while and cant find a suitable answer. I am a relative newb so i need things to be explained in its simplest of forms. i thank you guys in advance for your help and patience.

---

### Post by Rubi1200 on 2010-08-30
When you boot into Ubuntu go to the terminal and run the following commands:

```
sudo update-grub
```
```
sudo fdisk -l

```Lowercase L not 1

After running the first command reboot and see if you can get into osx; report any problems.

The second command gives us a better view of your drive setup.

Thanks.

---

### Post by cariboo on 2010-08-30
It is against Apples EULA to install OSX on non-Apple branded hardware. We don't support this type of activity. Thread Closed.

---

