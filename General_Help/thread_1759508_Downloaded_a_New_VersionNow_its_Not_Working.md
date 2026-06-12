---
title: "Downloaded a New Version/Now its Not Working"
date: 2011-05-15
forum: General Help
---

### Post by Sirsm0keall0t on 2011-05-15
Hello,

I have a problem that I need some help with. Im currently running Ubuntu/Linux on a R51 Think Pad with about 2G of hard drive space. 

I downloaded the updates that my system checks for every day and also the new version of Ubuntu for my computer. I also changed the settings in Power Management to read that my computer would never go to into suspend mode. It has been going into suspend mode every now and then and there is no way to escape. A simple reboot fixes that, but for the main problem it does not. When powering up it tries to load Ubuntu but it stops. It flashes the word ubuntu for a millisecond and then goes to blank screen. I can access my comp through SafeMode/RecoveryMode but I cannot access nor load ubuntu through regular sign on.

I have to admit that I may have done something wrong in doing something else. While the packages were downloading, I accidently powered down my computer. When powering back up, it did not give me the option to restart the upgrade of Ubuntu. So im thinking I may have removed some packages of the older version but never finished downloading the new ones.

What should I do? Sorry. Im not the smartest person in the world with computers but I am good at following directions.

Thanks in advance for your help

Mark

---

### Post by mörgæs on 2011-05-15
Hi, welcome to the fora.

A power-loss during installation is bad, and I would not spend long time before reinstalling a fresh Ubuntu. However, if you want to give it a chance, you could boot into recovery mode and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```Please post the error messages, if any.

---

